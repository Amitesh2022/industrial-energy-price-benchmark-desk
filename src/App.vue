<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">EnergyPriceEU<span>INDUSTRIAL BENCHMARKS</span></div><nav><RouterLink to="/">Price cases</RouterLink><RouterLink to="/insights">Benchmark guidance</RouterLink></nav><div class="health"><i /> Java energy price service connected</div></aside><main><header><div><span class="eyebrow">Compare industrial electricity and gas prices with accountable response actions</span><h1>Industrial Energy Price Benchmark Desk</h1></div><button @click="store.addOffer">Add price case</button></header><section class="summary"><article><small>Cases approved</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>Cases tracked</small><strong>{{ offers.length }}</strong><p>Shared benchmark view</p></article><article><small>Urgent price gaps</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
