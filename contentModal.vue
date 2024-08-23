<script setup lang="ts">
import { VueFinalModal } from 'vue-final-modal'


defineProps<{
  title?: string
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', modelValue: boolean): void
}>()


</script>

<template>
  <VueFinalModal id="modal"
    class="flex justify-center items-center"
    content-class="flex flex-col p-4 bg-white dark:bg-black rounded border border-gray-100 dark:border-gray-800"
    @update:model-value="val => emit('update:modelValue', val)"
  >
   
    <div class="modal-content">
      <div class="modal-header">
        <h4 class="modal-title" v-if="title">{{ title }} 1</h4>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="emit('update:modelValue', false)">
        <span aria-hidden="true">×</span>
        </button>
      </div>
      <div class="modal-body">
        <div class="form-check-inline mt-4">
            <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault1">
            <label class="form-check-label" for="flexRadioDefault1">
                일반
            </label>
            </div>
            <div class="form-check-inline">
            <input class="form-check-input" type="radio" name="flexRadioDefault" id="flexRadioDefault2" checked>
            <label class="form-check-label" for="flexRadioDefault2">
                이슈
            </label>&ensp;&ensp;
            <div class="btn-group">
                <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false"
                style="width:196px;">
                    dropdownMenu
                </button>
               
            </div>
        </div>

        <div class="btn-group mt-2">
            형식&ensp;
            <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Small button
            </button>
        </div>&ensp;&ensp;&ensp;

        <div class="btn-group mt-2">
            방송&ensp;
            <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Small button
            </button>
        </div>

         <div class="btn-group mt-2">
            부서&ensp;
            <button class="btn btn-sm btn-outline-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                Small button
            </button>
        </div>&ensp;&ensp;&ensp;

        <div class="btn-group mt-2">
            기자&ensp;
            <button class="btn btn-sm btn-outline-secondary text-toggle" type="button" data-bs-toggle="text" aria-expanded="false"
            style="width:115px;">
                Small button
            </button>
        </div>

         <div class="btn-group mt-2 ">
            제목&ensp;
            <button class="btn btn-sm btn-outline-secondary text-toggle" type="button" data-bs-toggle="text" aria-expanded="false" style="width:280px">
                Small buttonSmall button
            </button>
        </div>

        <div class="btn-group mt-2">
            상세<br>
            설명&ensp;
            <button class="btn btn-sm btn-outline-secondary textreas-toggle" type="button" data-bs-toggle="textreas" aria-expanded="false"
            style="width:280px; height: 100px">
                Small button
            </button>
        </div>
        <slot />
      </div>
      <div class="modal-footer justify-content-between">
        <button type="button" class="btn btn-default" data-dismiss="modal"  @click="emit('update:modelValue', false)">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>  
       
     
  </VueFinalModal>
</template>

<style>

#modal{
  width:400px;
  height:300px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 10%;
  font-size: 12px;

}

</style>