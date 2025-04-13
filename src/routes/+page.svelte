<script lang="ts">
	import interact from 'interactjs';
	import type { Action } from 'svelte/action';

	const position = $state({ x: 0, y: 0 });

	const draggable: Action<HTMLDivElement> = (node) => {
		const style = window.getComputedStyle(node);
		const matrix = new DOMMatrixReadOnly(style.transform);
		position.x = matrix.m41;
		position.y = matrix.m42;

		$effect(() => {
			const interaction = interact(node)
				.draggable({
					inertia: {
						resistance: 50
					},
					listeners: {
						start(event) {
							console.log(event.type, event.target, $state.snapshot(position));
						},
						move(event) {
							position.x += event.dx;
							position.y += event.dy;

							event.target.style.transform = `translate(${position.x}px, ${position.y}px)`;
						},
						end(event) {
							console.log(event.type, event.target, $state.snapshot(position));
						}
					}
				})
				.resizable({
					edges: { top: true, left: true, right: true, bottom: true },
					invert: 'none',
					inertia: {
						resistance: 30,
						minSpeed: 200,
						endSpeed: 100
					},
					listeners: {
						move: function (event) {
							position.x += event.deltaRect.left;
							position.y += event.deltaRect.top;

							Object.assign(event.target.style, {
								width: `${event.rect.width}px`,
								height: `${event.rect.height}px`,
								transform: `translate(${position.x}px, ${position.y}px)`
							});
						}
					}
				});

			return () => {
				interaction.unset();
			};
		});
	};

	$inspect(position);
</script>

<div
	class="m-4 h-24 min-h-20 w-36 min-w-28 touch-none rounded-xl bg-sky-400 p-4 text-white select-none"
	use:draggable
>
	Draggable Element
</div>
