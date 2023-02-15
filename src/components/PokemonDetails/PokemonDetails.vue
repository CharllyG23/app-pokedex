<template>
  <teleport to="body">
    <transition name="fade">
      <div v-if="modelValue" class="py-modal" @click="closeModal">
        <div class="py-modal__container">
          <div class="py-modal__content">
            <div class="py-modal__content--close">
							<button @click="closeModal">
                <svg width="20" height="20" viewBox="0 0 62 62" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M60.6267 1.4203C60.1917 0.984346 59.6749 0.638477 59.106 0.402491C58.5371 0.166505 57.9273 0.0450341 57.3114 0.0450341C56.6955 0.0450341 56.0856 0.166505 55.5167 0.402491C54.9478 0.638477 54.431 0.984346 53.996 1.4203L31 24.3693L8.00402 1.37327C7.56864 0.93789 7.05176 0.592527 6.48291 0.356901C5.91406 0.121274 5.30437 4.58748e-09 4.68865 0C4.07292 -4.58749e-09 3.46323 0.121274 2.89438 0.356901C2.32552 0.592527 1.80865 0.93789 1.37327 1.37327C0.93789 1.80865 0.592527 2.32552 0.356901 2.89438C0.121274 3.46323 -4.58748e-09 4.07292 0 4.68865C4.58749e-09 5.30437 0.121274 5.91406 0.356901 6.48291C0.592527 7.05176 0.93789 7.56864 1.37327 8.00402L24.3693 31L1.37327 53.996C0.93789 54.4314 0.592527 54.9482 0.356901 55.5171C0.121274 56.0859 0 56.6956 0 57.3114C0 57.9271 0.121274 58.5368 0.356901 59.1056C0.592527 59.6745 0.93789 60.1913 1.37327 60.6267C1.80865 61.0621 2.32552 61.4075 2.89438 61.6431C3.46323 61.8787 4.07292 62 4.68865 62C5.30437 62 5.91406 61.8787 6.48291 61.6431C7.05176 61.4075 7.56864 61.0621 8.00402 60.6267L31 37.6307L53.996 60.6267C54.4314 61.0621 54.9482 61.4075 55.5171 61.6431C56.0859 61.8787 56.6956 62 57.3114 62C57.9271 62 58.5368 61.8787 59.1056 61.6431C59.6745 61.4075 60.1913 61.0621 60.6267 60.6267C61.0621 60.1913 61.4075 59.6745 61.6431 59.1056C61.8787 58.5368 62 57.9271 62 57.3114C62 56.6956 61.8787 56.0859 61.6431 55.5171C61.4075 54.9482 61.0621 54.4314 60.6267 53.996L37.6307 31L60.6267 8.00402C62.4137 6.21701 62.4137 3.20731 60.6267 1.4203Z" fill="#22C55E"/>
                </svg>
							</button>
						</div>
            <div class="py-modal__content_body">
              <div class="image">
                <img :src="info.sprites.front_default" alt="pokemon front" width="110" />
                <img :src="info.sprites.back_default" alt="pokemon back" width="110" />
              </div>
              <h1 class="title">{{ formatStringUppercase(info.name) }}</h1>
              <div class="stats">
                <h2>Stats</h2>
                <div class="stats">
                  <div v-for="(item, index) in info.stats" :key="index">
                    <div class="stats_stat">
                      <span class="stats_stat__nam">{{ formatString(item.stat.name) }} </span>
                      <span class="stats_stat__base">{{ item.base_stat }} </span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
					</div>
				</div>
			</div>
		</transition>
	</teleport>
</template>
<script setup>
import { computed } from 'vue'

const emit = defineEmits(['update:modelValue'])

const props = defineProps({
	modelValue: { type: Boolean, default: false },
    info: { type: Object, default: {} },
})

const closeModal = () => {
	visibility.value = false
}

const formatStringUppercase = (str) => {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

const formatString = (str) => {
  return str.replace(/-/g, ' ');
}

const visibility = computed({
	get() {
		return props.modelValue
	},
	set(value) {
		emit('update:modelValue', value)
	},
})
</script>
<style lang="scss" scoped>
@import './style.scss';
</style>