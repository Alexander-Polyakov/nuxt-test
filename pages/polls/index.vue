<template>
  <div class="container">
    <div class="polls-form">
      <div class="polls-form__title">Добавить опрос</div>

      <div
        class="polls-item"
        v-for="(ItemPoll, KeyPoll) in pollsItems"
        :key="KeyPoll"
      >
        <div class='polls-item__header'>
          <div class="polls-item__left">
            <div class="polls-item__title"> Условие {{KeyPoll + 1}}</div>
          </div>
          <div class="polls-item__right">
            <select v-model="ItemPoll.type" @change="changeType($event, KeyPoll)">
              <option value="default">Выберите условие</option>
              <option value="age">Возраст респондента</option>
              <option value="card_type">Тип карты лояльности</option>
              <option value="card_status">Статус карты лояльности</option>
            </select>
          </div>
        </div>
        <div class="polls-item__main" v-if="ItemPoll.type != 'default'">
          <div class="polls-item__main-item" v-for="(PollValueItem, PollValueKey) in ItemPoll.content.selectedValues" :key="PollValueKey">
            <div class='polls-item__left' >
              <div class='polls-item__subtitle'>
                {{ItemPoll.content.title}} {{PollValueKey + 1}}
              </div>
              
            </div>
            <div class="polls-item__right" v-if="ItemPoll.content.type == 'select'">
                <select v-model="ItemPoll.content.selectedValues[PollValueKey]">
                  <option v-for="(valueItem, valueIndex, valueKey) in ItemPoll.content.values" :value="valueIndex" :key="valueKey">{{valueItem}}</option>
                </select>
            </div>
            <div class="polls-item__right" v-if="ItemPoll.content.type == 'range'">
                От <input type="text" v-model="ItemPoll.content.selectedValues[PollValueKey].min">
                До <input type="text" v-model="ItemPoll.content.selectedValues[PollValueKey].max">
            </div>
          </div>
          <div class='polls-item__footer'>
            <div class='polls-item__add-value' @click="addValue(ItemPoll)">Добавить {{ItemPoll.content.title}}</div>
          </div>
        </div>
        <div class='polls-item__remove-poll' @click="removePolls(KeyPoll)">Удалить условие</div>
      </div>
      <div class="polls-form__add" @click="addPolls()">
        Нажмите чтобы добавить новое условие выборки.
      </div> 
    </div>
  </div>
</template>

<script>
export default {
  layout: 'polls',
  data() {
    return {
      pollsItems: []
    }
  },
  methods: {
    addPolls() {
      this.pollsItems.push({
        type: 'default',
        content: ''
      })
    },
    removePolls(key) {
      this.pollsItems.splice(key, 1);
    },
    changeType(event, key){
      let value = event.target.value;
      let contentObj;
      switch(value){
        case 'age': 
          contentObj = {
            type: 'range',
            values: {
              min: '',
              max: ''
            },
            defaultValue: {min: 0, max: 0},
            selectedValues: [{min: 0, max: 0}],
            title: 'диапазон'
          }
          break
        case 'card_type': 
          contentObj = {
            type: 'select',
            values: {
              gold: 'Gold',
              plat: 'Platinum'
            },
            defaultValue: 'gold',
            selectedValues: ['gold'],
            title: 'тип'
          }
          break
        case 'card_status': 
          contentObj = {
            type: 'select',
            values: {
              active: 'Активна',
              not_active: 'Не активна'
            },
            defaultValue: 'active',
            selectedValues: ['active'],
            title: 'тип'
          }
          break
        default:
            break
      }
      this.pollsItems[key].content = contentObj
    },
    addValue(poll){ 
      let value = poll.content.defaultValue
      let type = poll.content.type
      switch(type){
        case 'range': 
          poll.content.selectedValues.push({min: 0, max: 0})
          break
        default:
          poll.content.selectedValues.push(value)
          break
      }
    }
  },
  
}
</script>
 
<style lang="sass">
  .polls-form__add
    display: block
</style>
 