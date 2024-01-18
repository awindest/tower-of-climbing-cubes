<!--
                       
╭━━╮╱╱╱╱╭╮╱╱╱╱╱╭╮╱╭╮╱╱╱╱╱╭╮            ━╮ ╭━
╰┫┣╯╱╱╱╱┃┃╱╱╱╱╭╯╰╮┃┃╱╱╱╱╱┃┃             | |
╱┃┃╭━╮╭━╯┣━━┳━┻╮╭╯┃┃╱╱╭━━┫╰━┳━━╮       ╱ o \
╱┃┃┃╭╮┫╭╮┃┃━┫━━┫┃╱┃┃╱╭┫╭╮┃╭╮┃━━┫      ╱_____\
╭┫┣┫┃┃┃╰╯┃┃━╋━━┃╰╮┃╰━╯┃╭╮┃╰╯┣━━┃     ╱    o  \  
╰━━┻╯╰┻━━┻━━┻━━┻━╯╰━━━┻╯╰┻━━┻━━╯    (__o______)  

Yet another science experiment from Indest Labs.

Recommend viewing in Visual Source Code.
Amit did a great job on this and it helped me learn scss to boot!

  The CodePen:
  https://codepen.io/amit_sheen/pen/JjzGGQR
  and youtube links for a follow-along:
  https://youtube.com/live/2gEZlTpVCBY
  https://www.youtube.com/watch?v=2gEZlTpVCBY
  
  which is based on a threejs cube:
  https://twitter.com/akella/status/1739936674228891989

  What did I do? I just replaced a lot of html with some loops.
-->
<div class="scene">
    {#each Array(12) as _, index (index)}
        <div class="column">
            {#each Array(6) as _, index (index)}
                <div class="box"><i></i><i></i><i></i><i></i><i></i><i></i></div>
            {/each}
        </div>
    {/each}
</div>

<style lang="scss">
    @use "sass:math"; // the '/' in scss will be deprecated so you should use math.div hence the import of sass:math

	.scene {
		position: relative;
		transform: rotateX(-30deg) rotateY(-60deg);
		font-size: 60px;
		animation: sceneRotate 60s infinite linear;

		@keyframes sceneRotate {
			from {
				transform: rotateX(-30deg) rotateY(0deg);
			}
			to {
				transform: rotateX(-30deg) rotateY(360deg);
			}
		}
	}

	$duration: 12s;

	.column {
		position: absolute;
		transform: rotateY(var(--ry)) translateX(2.8em);

		@for $i from 0 to 12 {
			&:nth-child(#{$i + 1}) {
				--ry: #{math.div(360deg, 12) * $i};

				.box {
					animation:
						boxRotate#{$i} $duration var(--delay) infinite ease-in-out,
						boxTop#{$i} $duration var(--delay) infinite step-end,
						boxTranslate $duration var(--delay) infinite linear;
				}
			}

			$p1: math.div(random(100), 100) * 40;
			$p2: $p1 + 4 + math.div(random(100), 100) * 4;
			$p3: $p2 + 2 + math.div(random(100), 100) * 2;
			$p4: $p3 + 2 + math.div(random(100), 100) * 2;
			$p5: $p4 + 2 + math.div(random(100), 100) * 2;
			$p6: $p5 + 2 + math.div(random(100), 100) * 2;
			$p7: $p6 + 4 + math.div(random(100), 100) * 4;

			@keyframes boxRotate#{$i} {
				0%,
				#{$p1}% {
					rotate: 0.25turn;
				}
				#{$p2}%,
				#{$p3}%,
				#{$p4}%,
				#{$p5}%,
				#{$p6}% {
					rotate: -0.25turn;
					animation-timing-function: step-end;
				}

				#{$p2}%,
				#{$p3}%,
				#{$p4}%,
				#{$p5}%,
				#{$p6}% {
					rotate: 0turn;
				}
				#{$p7}%,
				100% {
					rotate: -0.5turn;
				}
			}

			@keyframes boxTop#{$i} {
				0%,
				#{$p1}% {
					top: 0;
				}
				#{$p2}% {
					top: -1em;
				}
				#{$p3}% {
					top: -2em;
				}
				#{$p4}% {
					top: -3em;
				}
				#{$p5}% {
					top: -4em;
				}
				#{$p6}% {
					top: -5em;
				}
			}
		}
	}

	.box {
		position: absolute;
		width: 1em;
		height: 1em;
		transform-origin: top left;

		@for $i from 0 to 6 {
			&:nth-child(#{$i + 1}) {
				--delay: #{math.div($duration, -6) * $i};
			}
		}

		@keyframes boxTranslate {
			from {
				translate: 0 1em;
			}
			to {
				translate: 0 7em;
			}
		}

		i { // make the icon elements into a cube; quite clever
			--gap: 0.05em;
			position: absolute;
			inset: var(--gap);
			background-color: #000d;
            border: 2px royalblue solid;
			box-shadow: 0 0 0.5em royalblue inset;

			&:nth-child(1) {
				transform: translateZ(calc(0.5em - var(--gap)));
			}
			&:nth-child(2) {
				transform: rotateY(90deg) translateZ(calc(0.5em - var(--gap)));
			}
			&:nth-child(3) {
				transform: rotateY(180deg) translateZ(calc(0.5em - var(--gap)));
			}
			&:nth-child(4) {
				transform: rotateY(270deg) translateZ(calc(0.5em - var(--gap)));
			}
			&:nth-child(5) {
				transform: rotateX(270deg) translateZ(calc(0.5em - var(--gap)));
			}
			&:nth-child(6) {
				transform: rotateX(90deg) translateZ(calc(0.5em - var(--gap)));
			}
		}
	}
</style>
