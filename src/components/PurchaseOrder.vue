<template>
  <ContentPage>
    <div
      class="border-round-md bg-white border-200 shadow-1 border-1 p-3 w-10 mx-auto"
    >
      <div class="">
        <h1 class="text-center">Purchase Order</h1>
      </div>
      <div class="flex justify-content-between gap-4 mt-5 mr-5">
        <div class="w-5 grid gap-y-4">
          <Button class="w-6 btn-custom">Purchase Order No.</Button
          ><InputText class="input-custom w-6"></InputText>
          <Button class="mt-3 w-6 btn-custom">Purchase Order No.</Button>
          <Dropdown
            class="text-sm mt-3 w-6"
            id="country2"
            :options="countries"
            optionLabel="name"
            :filter="true"
            filterBy="name"
            :showClear="true"
            placeholder="Select a date"
          >
          </Dropdown>
          <Calendar
            class="w-6 mt-3"
            inputId="icon"
            v-model="date"
            :showIcon="true"
          />
          <div class="w-full">
            <Button
              class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
              label="Add more fields"
              icon="pi pi-plus"
            />
          </div>
        </div>
        <div class="w-5 flex justify-content-end align-items-center">
          <UploadFile />
          <TextInput type="number" />
        </div>
      </div>

      <div class="flex gap-4 my-5">
        <div class="w-6 px-4 pb-4 bg-cyan-50 border-round-xl shadow-1">
          <h2 class="mt-4">Order By</h2>
          <div
            class="border-1 p-3 border-500 border-round-md bg-white flex flex-column gap-4"
          >
            <Dropdown
              class="text-sm mt-3 w-full"
              v-model="selectcountry"
              :options="country"
              optionLabel="name"
              optionValue="code"
              placeholder="Select a Country"
            />
            <InputText
              class="input-custom w-full"
              placeholder="Your Bussiness/ Freelancer Name (Required)"
              required
            />
            <InputText
              class="input-custom w-full"
              placeholder="Address (Optional)"
            />
            <div class="flex gap-1">
              <InputText
                class="input-custom w-6"
                placeholder="City (Optional)"
              />
              <InputText
                class="input-custom w-6"
                placeholder="Postal Code/ Zip Code"
                required
              />
            </div>
            <InputText
              class="input-custom w-full"
              placeholder="State (Optional)"
            />
            <div class="">
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Email"
                icon="pi pi-envelope"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Phone Number"
                icon="pi pi-phone"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add GST"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add PAN"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add more fields"
                icon="pi pi-plus"
              />
            </div>
          </div>
        </div>
        <div class="w-6 px-4 pb-4 bg-cyan-50 border-round-xl shadow-1">
          <h2 class="mt-4">Order To</h2>
          <div
            class="border-1 p-3 border-500 border-round-md bg-white flex flex-column gap-4"
          >
            <CountryDropdown />

            <InputText
              class="input-custom w-full"
              placeholder="Your Bussiness/ Freelancer Name (Required)"
              required
            />
            <InputText
              class="input-custom w-full"
              placeholder="Address (Optional)"
            />
            <div class="flex gap-1">
              <InputText
                class="input-custom w-6"
                placeholder="City (Optional)"
              />
              <InputText
                class="input-custom w-6"
                placeholder="Postal Code/ Zip Code"
                required
              />
            </div>
            <InputText
              class="input-custom w-full"
              placeholder="State (Optional)"
            />
            <div class="">
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Email"
                icon="pi pi-envelope"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Phone Number"
                icon="pi pi-phone"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add GST"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add PAN"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add more fields"
                icon="pi pi-plus"
              />
            </div>
          </div>
        </div>
      </div>

      <div class="">
        <CheckboxInput label="Add Shipping Details" />
      </div>

      <div class="flex gap-4 my-5">
        <div class="w-6 px-4 pb-4 bg-cyan-50 border-round-xl shadow-1">
          <h2 class="mt-4">Shipped From</h2>
          <div
            class="border-1 p-3 border-500 border-round-md bg-white flex flex-column gap-4"
          >
            <Dropdown
              class="text-sm mt-3 w-full"
              v-model="selectcountry"
              :options="country"
              optionLabel="name"
              optionValue="code"
              placeholder="Select a Country"
            />
            <InputText
              class="input-custom w-full"
              placeholder="Your Bussiness/ Freelancer Name (Required)"
              required
            />
            <InputText
              class="input-custom w-full"
              placeholder="Address (Optional)"
            />
            <div class="flex gap-1">
              <InputText
                class="input-custom w-6"
                placeholder="City (Optional)"
              />
              <InputText
                class="input-custom w-6"
                placeholder="Postal Code/ Zip Code"
                required
              />
            </div>
            <InputText
              class="input-custom w-full"
              placeholder="State (Optional)"
            />
            <div class="">
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Email"
                icon="pi pi-envelope"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Phone Number"
                icon="pi pi-phone"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add GST"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add PAN"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add more fields"
                icon="pi pi-plus"
              />
            </div>
          </div>
        </div>
        <div class="w-6 px-4 pb-4 bg-cyan-50 border-round-xl shadow-1">
          <h2 class="mt-4">Shipped by</h2>
          <div
            class="border-1 p-3 border-500 border-round-md bg-white flex flex-column gap-4"
          >
            <CountryDropdown />

            <InputText
              class="input-custom w-full"
              placeholder="Your Bussiness/ Freelancer Name (Required)"
              required
            />
            <InputText
              class="input-custom w-full"
              placeholder="Address (Optional)"
            />
            <div class="flex gap-1">
              <InputText
                class="input-custom w-6"
                placeholder="City (Optional)"
              />
              <InputText
                class="input-custom w-6"
                placeholder="Postal Code/ Zip Code"
                required
              />
            </div>
            <InputText
              class="input-custom w-full"
              placeholder="State (Optional)"
            />
            <div class="">
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Email"
                icon="pi pi-envelope"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Phone Number"
                icon="pi pi-phone"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add GST"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add PAN"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add more fields"
                icon="pi pi-plus"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="flex gap-4 my-5">
        <div class="w-6 px-4 pb-4 bg-cyan-50 border-round-xl shadow-1">
          <h2 class="mt-4">Shipped by</h2>
          <div
            class="border-1 p-3 border-500 border-round-md bg-white flex flex-column gap-4"
          >
            <CountryDropdown />

            <InputText
              class="input-custom w-full"
              placeholder="Your Bussiness/ Freelancer Name (Required)"
              required
            />
            <InputText
              class="input-custom w-full"
              placeholder="Address (Optional)"
            />
            <div class="flex gap-1">
              <InputText
                class="input-custom w-6"
                placeholder="City (Optional)"
              />
              <InputText
                class="input-custom w-6"
                placeholder="Postal Code/ Zip Code"
                required
              />
            </div>
            <InputText
              class="input-custom w-full"
              placeholder="State (Optional)"
            />
            <div class="">
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Email"
                icon="pi pi-envelope"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add Phone Number"
                icon="pi pi-phone"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add GST"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add PAN"
                icon="pi pi-plus"
              />
              <Button
                class="bg-transparent py-2 px-4 text-gray-700 hover:text-gray-900 border-none border-noround outline-none btn-icon"
                label="Add more fields"
                icon="pi pi-plus"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="my-5 flex justify-content-between">
        <div class="">
          <Button
            label="Add GST"
            icon="pi pi-percentage"
            class="p-button-outlined p-button-secondary flex align-items-center"
          />
        </div>
        <div class="flex align-items-center gap-2">
          <label for="">Currency</label>
          <Button
            label="Indian Rupee"
            class="p-button-outlined p-button-secondary flex align-items-center"
          />
        </div>
        <div class="flex align-items-center gap-3">
          <Button
            label="Change Number Format"
            icon="pi pi-sort-numeric-down"
            class="p-button-outlined p-button-secondary flex align-items-center"
          />
          <Button
            label="Rename Add Fields"
            icon="pi pi-pencil"
            class="p-button-outlined p-button-secondary flex align-items-center"
          />
        </div>
      </div>
    </div>
  </ContentPage>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  components: {},
  props: {
    datatableConfig: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    let today = new Date();
    const date = ref();
    const selectcountry = ref();
    const displayBasic = ref(false);
    const openBasic = () => {
      displayBasic.value = true;
    };

    const closeBasic = () => {
      displayBasic.value = false;
    };
    const position = ref("center");
    const data = {
      isDeleteModalOpen: ref(false),
    };
    const responsiveOptions = ref([
      {
        breakpoint: "1400px",
        numMonths: 2,
      },
      {
        breakpoint: "1200px",
        numMonths: 1,
      },
    ]);
    return {
      date,
      selectcountry,
      responsiveOptions,
      displayBasic,
      openBasic,
      closeBasic,
      position,
    };
  },
});
</script>
