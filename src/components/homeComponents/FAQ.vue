<template>
  <div id="faq" class="widget">
    <h2 id="faqTitle">FAQ</h2>
    
<!--    Outputs faq objects dynamically, as defined by the 'faqs' object in the data.-->
    <div class="faqModule" v-for="faq in faqs">
      <div class="question" @click="expandFAQ(faq.id)">
        <span v-if="expanded != faq.id">▶</span>
        <span v-if="expanded == faq.id">▼</span>
        <span class="qText">{{ faq.question }}</span>
      </div>
      <transition name="wipe">
        <div class="answer" v-html="faq.answer" v-if="expanded == faq.id"></div>
      </transition>
    </div>
    <br><br>
    <p style="text-align:center;">
      Still have questions?  
      <router-link to="contact" id="contactLink">Let us know!</router-link>
    </p>
    
  </div>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {
      expanded: -1,
      faqs: [
        {
          id: 0,
          question: 'What is a hackathon?',
          answer: 'A hackathon is a weekend long event to meet smart creative people, make connections, learn, and build something awesome! <br><br> Attendes meet on Friday, make a team, and have 36 hours to build a tech-related project. There will be optional lessons and talks, sponsors looking to hire smart, motivated people, and tons of free stuff!',
        },
        {
          id: 1,
          question: 'Can I participate?',
          answer: 'If you\'re a high school student, a college student, or a recent college graduate, then yes!  KHE is attended by people of all skill levels and backgrounds.  You\'ll fit right in, and hopefully learn something.',
        },
        {
          id: 2,
          question: 'Sounds cool, but how much does it cost?',
          answer: '$0.00!!<br><br>Thanks to the generosity of our sponsors, we\'re able to put on events like this for <i>free</i>.  We even pay for your meals for the weekend, and can reimburse you for travel costs.  Make sure to thank our sponsors - we couldn\'t do it without them!',
        },
        {
          id: 3,
          question: 'What should I bring?',
          answer: 'Bring a laptop/something to hack on, a change of clothes, deoderant, a blanket/pillow, toiletries, deoderant, anything else you think you might use to complete your project, and deoderant.<br><br>We\'ll have an MLH hardware lab, which means we\'ll also have some cool hardware you can rent if you want!',
        },
        {
          id: 4,
          question: 'Do I need to come with a team?',
          answer: 'You can, but you don\'t have to! We\'ll have team building at the event.',
        },
        {
          id: 5,
          question: 'How many people per team?',
          answer: 'There\'s no hard limit, but the prizes are meant for teams of 4, so that\'s what we recommend.',
        },
      ]
    };
  },
  methods: {
    expandFAQ(id) {
      if (this.expanded === id) {
        this.expanded = -1;
      } else {
        this.expanded = id;
      }
    }
  }
};
</script>

<style scoped>
  
  #faqTitle {
    font-size: 50px;
  }
  
  #faq {
    background: white;
    font-size: 20px;
    line-height: 30px;
    color: black;
  }
  
  .faqModule {
    box-shadow: 1px 1px 10px rgba(0,0,0,.5);
    padding: 10px 20px 10px 20px;
    margin: 5px;
  }
  
  .question {
    width: 100%;
    cursor: pointer;
    font-weight: bold;
  }
  .answer {
    margin-top: 10px;
    border-top: 1px solid gray;
    padding-top: 10px;
    overflow: hidden;
    max-height: 300px;
  }
  
  #contactLink {
    color: black;
  }
  
  .qText {
    transition-duration: .4s;
  }
  .qText:hover {
    letter-spacing: 1px;
  }
  
/*  VUE TRANSITIONS*/
  
  .wipe-enter-active, .wipe-leave-active {
    transition: max-height .5s;
  }
  .wipe-enter, .wipe-leave-to {
    max-height: 0px;
  }

</style>

