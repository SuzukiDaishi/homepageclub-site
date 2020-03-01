<template>
<div :class="$style.wrapper">
    <CloseBox style="z-index:100" ref="closeBox"/>
    <cyber-box>
        <div :class="[$style.wrapper, $style.translucent_filter, $style.hero_center_wrapper]">
            <h1 :class="[$style.title, $style.glitch]" :data-text="dispTitle">
                {{ dispTitle }}
            </h1>
        </div>
    </cyber-box>
</div>
</template>

<script>
import anime from 'animejs'
import CyberBox from '~/components/atomis/CyberBox.vue'
import CloseBox from '~/components/atomis/CloseBox.vue'

export default {
    components: {
        CyberBox,
        CloseBox,
    },
    data() {
      return {
        title: 'ホームページ倶楽部',
        titleDispCount: 0,
        dispTitle: ''
      }
    },
    async mounted() {
      await this.sleep(1000)
      await this.typing()
      await this.sleep(1000)
      await this.$refs.closeBox.close()
      this.$router.push('/home')
    },
    methods: {
      async typing() {
        let self = this
        return anime({
          targets: self,
          titleDispCount: [0, self.title.length],
          easing: 'easeInOutSine',
          round: 1,
          duration: 3000,
          update() {
            self.dispTitle = self.title.slice(0, self.titleDispCount)
          }
        }).finished
      },
      async sleep(waitSeconds, someFunction=()=>{}) {
        return new Promise(resolve => {
          setTimeout(() => {
            resolve(someFunction())
          }, waitSeconds)
        })
      } 
    }
}
</script>

<style lang="scss" module>
@import 'assets/scss/settings.scss';

.wrapper {
    width: 100%;
    height: 100%;
}
.hero_center_wrapper {
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
h1.title {
    font-size: 2em;
    @include pc {
        font-size: 4em;
    }
    @include tab {
        font-size: 4em;
    }
}
.translucent_filter {
    background: radial-gradient(rgba(0,0,0,1), rgba(0,0,0,0.8), rgba(0,0,0,0));
}


@mixin glitchCopy { 
		content: attr(data-text);
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
}

.glitch {
	position: relative;
	color: white;
	font-size: 4em;
	letter-spacing: .5em;
	animation: glitch-skew 1s infinite linear alternate-reverse;
	
	&::before{
        @include glitchCopy;
		left: 2px;
		text-shadow: -2px 0 #ff00c1;
		clip: rect(44px, 450px, 56px, 0);
		animation: glitch-anim 5s infinite linear alternate-reverse;
	}
	
	&::after {
		@include glitchCopy;
		left: -2px;
		text-shadow: -2px 0 #00fff9, 2px 2px #ff00c1;
		animation: glitch-anim2 1s infinite linear alternate-reverse;
	}
}

@keyframes glitch-anim {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100)+px, 9999px, random(100)+px, 0);
			transform: skew((random(100) / 100) + deg);
    }
  }
}

@keyframes glitch-anim2 {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100)+px, 9999px, random(100)+px, 0);
			transform: skew((random(100) / 100) + deg);
    }
  }
}

@keyframes glitch-skew {
  $steps: 10;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      transform: skew((random(10) - 5) + deg);
    }
  }
}

</style>
