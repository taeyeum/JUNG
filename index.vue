<template>
    <Panel title="이슈관리">
      <div class="row">
        <div class="col-lg-12">
          <div class="card card-primary" style="height:800px;">
            <div class="card-header">
              <h3 class="card-title">검색바</h3>
            </div>
            <div class="card-body row">
              <div class="col-lg-3">
                <div class="input-group">
                  <label>작성일</label> &ensp;
                  <div class="row">
                    <div class="col-10">
                      <div
                        class="input-group date"
                        id="reservationdate"
                        data-target-input="nearest"                                               
                      >
                        <input
                          type="text"
                          class="form-control form-control-sm datetimepicker-input"
                          data-target="#reservationdate"
                        />
                        <div
                          class="input-group-append"
                          data-target="#reservationdate"
                          data-toggle="datetimepicker"
                        >
                        <div class="input-group-text">
                          <i class="fa fa-calendar"></i>
                        </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="col-lg-4">
                <div class="form-check">
                  <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" style="width:20px; height:20px;">
                  &ensp;
                  <label class="form-check-label" for="flexCheckDefault">
                    삭제데이터
                  </label>
                </div>             
              </div>

              <div class="col-lg-5">
                <div class="form-group">  
                <button class="btn btn-info btn-sm mr-2 mb-2"> 
                    신규
                </button>
                <button @click="() => open()" class="btn btn-info btn-sm mr-2 mb-2" >
                    복사
                </button><ModalsContainer/>

                <button class="btn btn-info btn-sm mr-2 mb-2">
                  새로고침
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">              
                    저장
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">
                  완료
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">              
                  완료취소
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">              
                  삭제
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">              
                  삭제취소
                </button>
                <button class="btn btn-info btn-sm mr-2 mb-2">
                    <i class="fas fa-print"></i>
                    인쇄
                </button>
           
                </div>
              </div>
            </div>
            <div class="row">
                <div class="col-lg-12">
                <ag-grid-vue
                    :columnDefs="columnDefs"
                    :modules="modules"
                    :rowData="rowData"
                    :groupHeaders="true"
                    :defaultColDef="defaultColDef"
                    class="ag-theme-alpine"
                    style="flex: 1 1 auto; height: 670px; "
                >
                </ag-grid-vue>
                </div>
            </div>
     
        
     
            <!-- /.col -->
          </div>
        </div>
      </div>

    </Panel>
  </template>
  <script setup lang="ts">

  import { Panel } from "../../components";
  import { ref } from "vue";
  import "@ag-grid-community/styles/ag-grid.css";
  import "@ag-grid-community/styles/ag-theme-alpine.css";
  import { ClientSideRowModelModule } from "@ag-grid-community/client-side-row-model";
  import { AgGridVue } from "@ag-grid-community/vue3";
  
  import CellComponentRenderer from "../../components/grid/CellComponentRenderer.vue";
  import CellComponentEditor from "../../components/grid/CellComponentEditor.vue";
  import DateComponent from "../../components/grid/DateComponent.vue";
  import HeaderGroupComponent from "../../components/grid/HeaderGroupComponent.vue";

  import { ModalsContainer, useModal } from 'vue-final-modal'
  import issModal from '../../components/issue/issueModal.vue'

  
  const { open } = useModal({
  component: issModal,
  attrs: {
    title: '이슈복사',
  },
  slots: {
    default: '<p>The content of the modal</p>',
  },
})
  
  const modules = ref([ClientSideRowModelModule]);
  
  const defaultColDef = {
    flex: 1,
  };
  
  const columnDefs = ref([
    {
      headerName: "기본 헤더",
      headerGroupComponent: "HeaderGroupComponent",
      headerClass: "text-center",
      children: [
        { field: "no", headerName: "No", cellStyle: { textAlign: "center" } },
        {
          field: "",
          headerName: "제목",
          cellStyle: { textAlign: "left" },
          autoSizeStrategy: { type: "fitCellContents" },
        },
        {
          field: "",
          headerName: "",
          minWidth: 50,
          maxWidth: 50,
          suppressSizeToFit: true,
        },
        {
          field: "",
          headerName: "게시여부",
          cellStyle: { textAlign: "center" },
          suppressSizeToFit: true,
        },
        {
          field: "",
          headerName: "작성자",
          cellStyle: { textAlign: "center" },
          suppressSizeToFit: true,
        },
        {
          field: "",
          headerName: "작성일시",
          cellStyle: { textAlign: "center" },
          suppressSizeToFit: true,
        },

      ],
    },
  ]);
  
  const rowData = ref([
    {
      no: 10,
      compilation: "편집",
      program: "프로그램명1",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 9,
      compilation: "편집",
      program: "프로그램명2",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 8,
      compilation: "편집",
      program: "프로그램명3",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 7,
      compilation: "편집",
      program: "프로그램명4",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 6,
      compilation: "편집",
      program: "프로그램명5",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 5,
      compilation: "편집",
      program: "프로그램명6",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 4,
      compilation: "편집",
      program: "프로그램명7",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 3,
      compilation: "편집",
      program: "프로그램명8",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 2,
      compilation: "편집",
      program: "프로그램명9",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
    {
      no: 1,
      compilation: "편집",
      program: "프로그램명10",
      broadcastDate: new Date(2000, 0, 1),
      startTime: "11:11",
      endTime: "12:11",
      studio: "스튜디오1",
      control: "2부조",
      article: 3,
      broadcast: "방송완료",
    },
  ]);
  
  defineExpose({
    CellComponentRenderer,
    CellComponentEditor,
    agDateInput: DateComponent,
    HeaderGroupComponent,
  });


  </script>

  <style>

</style>