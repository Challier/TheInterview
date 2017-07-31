<template>
  <div class="hello">   
    <v-container fluid>
      <v-layout row wrap>
        <v-flex xs4 offset-xs2>
          <multiselect 
            id="companies"
            v-model="valCompanies" 
            :options="companies" 
            :searchable="true" 
            :close-on-select="false" 
            :show-labels="false" 
            :multiple="true"
            placeholder="Companies">
          </multiselect>
        </v-flex>
        <v-flex xs4>
          <multiselect 
            id="categories"
            v-model="valCategories" 
            :options="categories" 
            :searchable="true" 
            :close-on-select="false" 
            :show-labels="false" 
            :multiple="true"
            placeholder="Categories">
          </multiselect>
        </v-flex>
        <v-flex xs8 offset-xs2>
          <div v-for="question in questions" v-show="(valCompanies.indexOf(question.Company) !== -1) && (valCategories.indexOf(question.Category) !== -1)">
            <v-card class="mt-3">
              <v-card-actions>
                <v-btn flat :class="question.Color">{{ question.Company }}</v-btn>
                <v-btn flat class="grey--text">{{ question.Category }}</v-btn>
              </v-card-actions>
              <v-card-text>
                {{ question.Question }}
              </v-card-text>
            </v-card>
          </div>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import Multiselect from 'vue-multiselect'

export default {
  name: 'hello',
  components: { Multiselect },
  data () {
    return {
      questions: [
        {'Company': 'Facebook', 'Category': 'Behavior', 'Question': 'What\'s something you hold true but that most people you consider smart disagree on?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Logic', 'Question': 'How many birthday posts occur on Facebook on a given day?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Logic', 'Question': "You're about to get on a plane to Seattle. You want to know if you should bring an umbrella. You call 3 random friends of yours who live there and ask each independently if it's raining. Each of your friends has a 2/3 chance of telling you the truth and a 1/3 chance of messing with you by lying. All 3 friends tell you that 'Yes' it is raining. What is the probability that it's actually raining in Seattle?", 'Color': 'blue blue--text'},
        {'Company': 'Uber', 'Category': 'Business', 'Question': "What metrics would you use to track whether Uber's strategy of using paid advertising to acquire customers works? How would you then figure out an acceptable cost of customer acquisition?", 'Color': 'blue blue--text'},
        {'Company': 'Google', 'Category': 'Logic', 'Question': 'How many golf balls can fit in a school bus?', 'Color': 'red red--text'},
        {'Company': 'Amazon', 'Category': 'Business', 'Question': 'You work in a bank. By referring to data held by the bank only, you would like to find out whether a client is associated with someone outside of the bank. What data would you look at, and why?', 'Color': 'orange orange--text'},
        {'Company': 'Google', 'Category': 'Logic', 'Question': 'How many golf balls can fit in a school bus?', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Logic', 'Question': 'You\'re the captain of a pirate ship and your crew gets to vote on how the gold is divided up. If fewer than half of the pirates agree with you, you die. How do you recommend apportioning the gold in such a way that you get a good share of the booty, but still survive?', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Logic', 'Question': 'You are given 2 eggs, you have access to a 100-story building. Eggs can be very hard or very fragile means it may break if dropped from the first floor or may not even break if dropped from 100th floor. Both eggs are identical. You need to figure out the highest floor of a 100-story building an egg can be dropped without breaking. The question is how many drops you need to make. You are allowed to break 2 eggs in the process.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Behavior', 'Question': 'Explain a database in three sentences to your eight-year-old nephew.', 'Color': 'red red--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'How would you measure the health of Mentions, Facebook\'s app for celebrities? How can FB determine if it\'s worth it to keep using it? If a celebrity starts to use Mentions and begins interacting with their fans more, what part of the increase can be attributed to a celebrity using Mentions, and what part is just a celebrity wanting to get more involved in fan engagement?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'If 70% of Facebook users on iOS use Instagram, but only 35% of Facebook users on Android use Instagram, how would you investigate the discrepancy?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'If a PM says that they want to double the number of ads in Newsfeed, how would you figure out if this is a good idea or not?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'How do you map nicknames (Pete, Andy, Nick, Rob, etc) to real names?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'Facebook sees that likes are up 10% year over year, why could this be?', 'Color': 'blue blue--text'},
        {'Company': 'Facebook', 'Category': 'Business', 'Question': 'How many high schools that people have listed on their profiles are real? How do we find out, and deploy at scale, a way of finding invalid schools?', 'Color': 'blue blue--text'},
        {'Company': 'Amazon', 'Category': 'Behavior', 'Question': 'How would you introduce AWS in an elevator pitch?', 'Color': 'orange orange--text'},
        {'Company': 'Amazon', 'Category': 'Behavior', 'Question': 'Do you think you\'ll reach a point where you storm off the floor and never return?', 'Color': 'orange orange--text'},
        {'Company': 'Amazon', 'Category': 'Business', 'Question': 'Walk me through how Amazon Kindle books would be priced.', 'Color': 'orange orange--text'},
        {'Company': 'Amazon', 'Category': 'Behavior', 'Question': 'Which Amazon leadership principle do you resonate most with?', 'Color': 'orange orange--text'},
        {'Company': 'Google', 'Category': 'Logic', 'Question': 'If the probability of observing a car in 30 minutes on a highway is 0.95, what is the probability of observing a car in 10 minutes (assuming constant default probability)?', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Behavior', 'Question': 'Explain a database in three sentences to your eight-year-old nephew.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Business', 'Question': 'Name three non-Google websites that you visit often and like. What do you like about the user interface and design? Choose one of the three sites and comment on what new feature or project you would work on. How would you design it?', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Business', 'Question': 'Design the SQL database tables for a car rental database.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Coding', 'Question': 'Suppose you have an NxN matrix of positive and negative integers. Write some code that finds the sub-matrix with the maximum sum of its elements.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Coding', 'Question': 'You are given an array [a1 To an] and we have to construct another array [b1 To bn] where bi = a1*a2*…*an/ai. you are allowed to use only constant space and the time complexity is O(n). No divisions are allowed.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Coding', 'Question': 'Given two binary trees, write a compare function to check if they are equal or not. Being equal means that they have the same value and same structure.', 'Color': 'red red--text'},
        {'Company': 'Google', 'Category': 'Coding', 'Question': 'Write a program for displaying the ten most frequent words in a file such that your program should be efficient in all complexity measures.', 'Color': 'red red--text'}
      ],
      valCompanies: [],
      companies: ['Amazon', 'Facebook', 'Google', 'Uber'],
      valCategories: [],
      categories: ['Behavior', 'Business', 'Coding', 'Logic']
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style type="text/css">
#textbox {
    display: flex;
    justify-content: space-between;
}
</style>
<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>
