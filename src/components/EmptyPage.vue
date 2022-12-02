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
  <!-- <div>
    <template>
    <ContentPage>
        <div class="grid">
            <div class="col-12 md:col-9">
                <div class="flex align-items-center gap-2 -mt-3 align-self-center">
                    <h3 class="">
                        Order Number
                        <span
                            class="text-blue-500 cursor-pointer hover:underline"
                            @click="orderIdClicked"
                            v-tooltip.top="order.order_datetime"
                            >#{{ order.order_id }}
                        </span>
                    </h3>
                </div>
                <div class="col-12 md:col-9 p-0 w-full">
                    <div class="grid">
                        <div class="col-12 md:col-6">
                            <Card>
                                <template #header>Order Details</template>
                                <template #body>
                                    <ul class="list-none p-0 m-0">
                                        <li class="flex p-0">
                                            <span class="label-info text-mute">Ship By</span>
                                            <span class="label-info white-space-nowrap overflow-hidden mr-2">{{
                                                order.ship_by
                                            }}</span>
                                        </li>
                                        <li class="flex p-0">
                                            <span class="label-info text-mute">Purchased date</span>
                                            <span
                                                class="label-info white-space-nowrap overflow-hidden mr-2"
                                                v-tooltip.top="order.order_datetime"
                                                >{{ order.ship_by }}</span
                                            >
                                        </li>
                                    </ul>
                                </template>
                            </Card>
                        </div>
                        <div class="col-12 md:col-6">
                            <Card class="h-full">
                                <template #header> Ship To </template>
                                <template #header-description> </template>
                                <template #body>
                                    <span v-if="order.delivery_address.address_line_1" class="label-info pl-3"
                                        >{{ order.delivery_address.address_line_1 }},</span
                                    >
                                    <span v-if="order.delivery_address.city" class="label-info pl-3">
                                        {{ order.delivery_address.city }},</span
                                    >
                                    <span v-if="order?.delivery_address?.state" class="label-info pl-3">
                                        {{ order?.delivery_address?.state }}</span
                                    >
                                    <span v-if="order?.delivery_address?.zip_code" class="label-info pl-3"
                                        >{{ order?.delivery_address?.zip_code }},</span
                                    >
                                    <span v-if="order?.delivery_address?.country" class="label-info pl-3">
                                        {{ order?.delivery_address?.country }}</span
                                    >
                                </template>
                            </Card>
                        </div>
                    </div>
                </div>
                <div class="col-12 md:col-9 p-0 w-full">
                    <div class="grid">
                        <div class="col-12 md:col-8">
                            <Card>
                                <template #header>Order Summery</template>
                                <template #header-description> </template>
                                <template #body>
                                    <ul class="list-none p-0 m-0 grid">
                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Ship By</span>
                                            <span
                                                class="mb-2 w-full line-height-3 white-space-nowrap overflow-hidden mr-2 text-green-500 font-semibold"
                                                >{{ order.ship_by }}</span
                                            >
                                        </li>
                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Purchased date</span>
                                            <span
                                                class="label-info white-space-nowrap overflow-hidden mr-2"
                                                v-tooltip.top="order.order_datetime"
                                                >{{ order.order_datetime }}</span
                                            >
                                        </li>

                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Shipping Service:</span>
                                            <span class="label-info">{{ order.shipping_service }}</span>
                                        </li>
                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Fulfillment:</span>
                                            <span class="label-info">{{ order.fulfillment_channel }}</span>
                                        </li>
                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Status:</span>
                                            <span class="label-info">
                                                <span
                                                    v-if="order.order_status == 'Shipped'"
                                                    class="inline-block text-green-600 font-semibold border-2 border-round-md pt-0.5 px-2"
                                                    ><font-awesome-icon icon="fa-solid fa-truck" />
                                                    {{ order.order_status }}</span
                                                >
                                                <span
                                                    v-if="order.order_status == 'Pending'"
                                                    class="inline-block text-yellow-600 font-semibold border-1 border-round-md pt-0.5 px-2"
                                                >
                                                    <span class="flex align-items-center gap-1"
                                                        ><i class="pi pi-exclamation-circle"></i>
                                                        {{ order.order_status }}</span
                                                    >
                                                </span>
                                                <span
                                                    v-if="order.order_status == 'Canceled'"
                                                    class="inline-block text-red-600 font-semibold border-2 border-round-md pt-0.5 px-2"
                                                >
                                                    <span class="flex align-items-center gap-1"
                                                        ><i class="pi pi-times"></i>
                                                        {{ order.order_status }}
                                                    </span></span
                                                ></span
                                            >
                                        </li>

                                        <li class="flex col-6 p-0">
                                            <span class="label-info text-mute">Sales Channel: </span>
                                            <span
                                                v-if="order.sales_channel == 'Amazon.com'"
                                                class="label-info flex gap-1"
                                                ><img class="w-1rem h-1rem" src="\images\images\USA.png" alt="USA" />
                                                {{ order.sales_channel }}</span
                                            >
                                            <span
                                                v-if="order.sales_channel == 'Amazon.ca'"
                                                class="label-info flex gap-1"
                                                ><img class="w-1rem h-1rem" src="\images\images\canada.png" alt="CA" />
                                                {{ order.sales_channel }}</span
                                            >
                                        </li>
                                    </ul>
                                </template>
                            </Card>
                        </div>
                        <div class="col-12 md:col-4">
                            <Card class="h-full">
                                <template #header> Ship To </template>
                                <template #header-description> </template>
                                <template #body>
                                    <span v-if="order.delivery_address.address_line_1" class="label-info pl-3"
                                        >{{ order.delivery_address.address_line_1 }},</span
                                    >
                                    <span v-if="order.delivery_address.city" class="label-info pl-3">
                                        {{ order.delivery_address.city }},</span
                                    >
                                    <span v-if="order?.delivery_address?.state" class="label-info pl-3">
                                        {{ order?.delivery_address?.state }}</span
                                    >
                                    <span v-if="order?.delivery_address?.zip_code" class="label-info pl-3"
                                        >{{ order?.delivery_address?.zip_code }},</span
                                    >
                                    <span v-if="order?.delivery_address?.country" class="label-info pl-3">
                                        {{ order?.delivery_address?.country }}</span
                                    >
                                </template>
                            </Card>
                        </div>
                    </div>
                </div>
                <Card class="mt-2 mb-3">
                    <template #header>
                        <div>Product Details</div>
                    </template>
                    <template #header-description> </template>
                    <template #body>
                        <div class="w-full overflow-auto md:overflow-hidden">
                            <table class="">
                                <tr class="grid text-left border-bottom-1 border-gray-300">
                                    <th class="col-3 pt-2 pb-3">Item Summery</th>
                                    <th class="col-2 pt-2 pb-3">Listing Id</th>
                                    <th class="col-2 pt-2 pb-3">Item Id</th>
                                    <th class="col-1 pt-2 pb-3">Qty</th>
                                    <th class="col-2 pt-2 pb-3">Price</th>
                                    <th class="col-2 pt-2 pb-3">Total Price</th>
                                </tr>
                                <tr class="grid pt-2 overflow-hidden">
                                    <td class="col-3 flex align-items-center gap-2">
                                        <img
                                            class="w-3rem"
                                            src="https://img.freepik.com/free-vector/red-clipart-flower-t-shirt-print_1305-5002.jpg?"
                                            alt=""
                                        />
                                        <div>
                                            <div class="font-bold">Lorem ipsum</div>
                                            <div class="">
                                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Corporis,
                                                corrupti.
                                            </div>
                                        </div>
                                    </td>
                                    <td class="col-2 p-3 overflow-hidden align-self-center">1324234</td>
                                    <td class="col-2 p-3 overflow-hidden align-self-center">
                                        123423422224234234242423423
                                    </td>
                                    <td class="col-1 p-3 align-self-center">1</td>
                                    <td class="col-2 p-3 overflow-hidden align-self-center">$12.22</td>
                                    <td class="col-2 p-3 overflow-hidden align-self-center">$1233.3</td>
                                </tr>
                            </table>
                        </div>
                    </template>
                </Card>
                <PrimeTable :config="datatableConfig" :link="route('order.items.datatable', order.id)"> </PrimeTable>
            </div>
            <div class="col-12 md:col-3">
                <Card class="mb-3">
                    <template #header> Sales Summery</template>
                    <template #body>
                        <ul class="list-none p-0 m-0">
                            <li class="flex">
                                <span class="label-info text-mute">Items total:</span>
                                <span class="label-info text-right">{{ order.order_total }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Mfg total:</span>
                                <span class="label-info text-right">{{ order.mfg_total }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Amazon Fees:</span>
                                <span class="label-info text-right">{{ order.amazon_fees }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Tax total:</span>
                                <span class="label-info text-right">{{ order.tax_total }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Promotion total:</span>
                                <span class="label-info text-right">{{ order.promotion_total }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Refunded amount:</span>
                                <span class="label-info text-right">{{ order.refunded_amount }}</span>
                            </li>
                        </ul>
                    </template>
                    <template #footer>
                        <ul class="list-none p-0 m-0 font-bold">
                            <li class="flex">
                                <span class="label-info text-mute">Profit:</span>
                                <span class="label-info text-right">{{ order.grand_total }}</span>
                            </li>
                        </ul></template
                    >
                </Card>
                <Card class="mb-3">
                    <template #header> Customer Details</template>
                    <template #body>
                        <ul class="list-none p-0 m-0">
                            <li class="flex">
                                <span class="label-info text-mute">Name</span>
                                <span class="label-info pl-3">{{ order.customer_name }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Email</span>
                                <span class="label-info pl-3">{{ order.customer_email }}</span>
                            </li>
                            <li class="flex">
                                <span class="label-info text-mute">Phone no.</span>
                                <span class="label-info pl-3">{{ order.customer_phone }}</span>
                            </li>
                        </ul>
                    </template>
                </Card>
            </div>
        </div>
    </ContentPage>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    props: {
        order: {
            type: Object,
            required: true,
        },
        datatableConfig: {
            type: Object,
            required: true,
        },
    },
    setup(props) {
        const orderIdClicked = () => {
            window.open('https://sellercentral.amazon.com/orders-v3/order/' + props.order.order_id);
        };
        return { orderIdClicked };
    },
});
</script>

  </div> -->
</template>
<template>
<div></div>
    <!-- <div class="surface-card p-3 shadow-2 border-round-md">
        <div
            class="border-bottom-1 border-dashed border-x-none border-top-none surface-border px-3 pb-2"
            v-if="$slots['header']"
        >
            <h3 class="m-0"><slot name="header"> </slot></h3>
        </div>
        <div class="surface-border border-round px-3 pt-2 pb-0" v-if="$slots['body']">
            <slot name="body"> </slot>
        </div>
        <div
            class="border-top-1 border-dashed border-x-none border-bottom-none surface-border border-round mt-2 px-3 pt-2"
            v-if="$slots['footer']"
        >
            <slot name="footer"></slot>
        </div>
    </div> -->
    <!-- <div>
      <script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'Card',
});
</script>
    </div> -->
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
