<template>
<GridLayout columns='*' rows='30, 50, auto'>
  <label row='0' class="big-text">ПОУЧИТЬСЯ</label>
  <GridLayout row='1' columns='*, *, *' rows='20, 30'>
    <label class='text' col='0' row='0'>голод ({{hunger}}/100)</label>
    <Progress width='30%' col='0' row='1' :value="hunger" maxValue="100"/>
    <label class='text' col='1' row='0'>настроение ({{mood}}/100)</label>
    <Progress width='30%' col='1' row='1' :value="mood" maxValue="100" />
    <label class='text' col='3' row='0'>здоровье ({{health}}/100)</label>
    <Progress width='30%' col='2' row='1' :value="health" maxValue="100"/>
  </GridLayout>
  <StackLayout v-if="hunger>0 || health>0 || mood>0" row='2' width='' orientation='vertical'>
    <Button v-if="edTierTwoGtr == false" class="button" text=">образование lvl_1 (1000р)" @tap="edTierTwoAct()"/>
    <Button v-else class="button" text=">образование lvl_1  (изучено)"/>
    <Button v-if="edTierThreeGtr == false" class="button" text=">образование lvl_2 (50000р)" @tap="edTierThreeAct()"/>
    <Button v-else class="button" text=">образование lvl_2 (изучено)"/>
    <Button v-if="edTierFourGtr == false" class="button" text=">образование lvl_3 (100000р)" @tap="edTierFourAct()"/>
    <Button v-else class="button" text=">образование lvl_3 (изучено)"/>
    <Button v-if="edTierFiveGtr == false" class="button" text=">образование lvl_4 (500000р)" @tap="edTierFiveAct()"/>
    <Button v-else class="button" text=">образование lvl_4 (изучено)"/>
  </StackLayout>
  <Label textWrap='true' row='2' v-else class="big-text" text='видимо, какой-то из параметров упал  настолько низко, что смерть настигла сего аватара'/>
</GridLayout>
</template>

<script>
import {mapGetters, mapActions, mapMutations, mapState} from 'vuex';

export default {
  computed: mapGetters(['rub', 'hunger', 'health', 'mood', 'edTierTwoGtr', 'edTierThreeGtr', 'edTierFourGtr', 'edTierFiveGtr']),
  methods:{
      onCloseTap: function(){
        this.$modal.close()
      },
      ...mapActions(['edTierTwoAct', 'edTierThreeAct', 'edTierFourAct', 'edTierFiveAct'])
  }
}
</script>