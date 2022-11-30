<script>
import { defineComponent, ref, computed } from "vue";
import { createPopper } from "@popperjs/core";

export default defineComponent({
  name: "Tooltip",
  props: {
    placement: String,
  },
  setup(props) {
    const button = ref(null);
    const tooltip = ref(null);

    const popperInstance = computed(() => {
      return createPopper(button.value, tooltip.value, {
        placement: props.placement, //'bottom',
        modifiers: [
          {
            name: "offset",
            options: {
              offset: [0, 10],
            },
          },
        ],
        strategy: "absolute",
      });
    });

    const insertElement = (btn, tip) => {
      button.value = btn;
      tooltip.value = tip;
    };

    const handleShow = (e) => {
      if (button.value === null && tooltip.value === null) {
        insertElement(
          e.target,
          e.target.parentElement.querySelector(".tooltipText")
        );
      }
      tooltip.value.setAttribute("data-show", "");
      popperInstance.value.update();
    };

    const handleHide = (e) => {
      if (button.value === null && tooltip.value === null) {
        insertElement(
          e.target,
          e.target.parentElement.querySelector(".tooltipText")
        );
      }
      tooltip.value.removeAttribute("data-show");
    };

    return {
      handleShow,
      handleHide,
    };
  },
});
</script>

<template>
  <div class="tooltip">
    <button
      type="button"
      class="button"
      aria-describedby="tooltip"
      @mouseenter="handleShow($event)"
      @mouseleave="handleHide($event)"
      @focus="handleShow($event)"
      @blur="handleHide($event)"
      placement="bottom"
    >
      Tooltip {{ placement }}
    </button>
    <div class="tooltipText" role="tooltip">
      The {{ placement }} of tooltip placement
      <div class="tooltipArrow" data-popper-arrow></div>
    </div>
  </div>
</template>

<style scoped>
.button {
  appearance: none;
  border: 1px solid rgba(0, 0, 0, 0.25);
  background-color: seagreen;
  border-radius: 5px;
  padding: 0.75rem;
  font-size: 12pt;
  color: white;
}

.tooltipText {
  background-color: #333;
  color: white;
  padding: 7px 10px;
  border-radius: 4px;
  font-size: 13px;
  display: none;
}

.tooltipText[data-show] {
  display: block;
}

.tooltipArrow,
.tooltipArrow::before {
  position: absolute;
  width: 8px;
  height: 8px;
  background: inherit;
}

.tooltipArrow {
  visibility: hidden;
}

.tooltipArrow::before {
  visibility: visible;
  content: "";
  transform: rotate(45deg);
}

.tooltipText[data-popper-placement^="top"] > .tooltipArrow {
  bottom: -4px;
}

.tooltipText[data-popper-placement^="bottom"] > .tooltipArrow {
  top: -4px;
}

.tooltipText[data-popper-placement^="left"] > .tooltipArrow {
  right: -4px;
}

.tooltipText[data-popper-placement^="right"] > .tooltipArrow {
  left: -4px;
}
</style>
