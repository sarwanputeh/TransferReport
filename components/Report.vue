import html2pdf from 'html2pdf.js';

function exportPDF() {
  try {
    html2pdf().set({
      margin: [30, 25, 10, 10],
      jsPDF: { unit: "mm", format: "a4", orientation: "portrait" },
      mode: { mode: ["avoid-all", "css", "legacy"] },
      html2canvas: { dpi: 1200, scale: 12 },
      filename: "reportname" + Date.now() + ".pdf",
    }).from(document.getElementById("element-pdfreport")).save();
  } catch (error) {
    console.log(error);
  }
}

document.querySelector(".btn").addEventListener("click", exportPDF);
//this type script to java script 
import html2pdf from 'html2pdf.js';

export default {
    props: {
        ContractNo: [String, Number],
        LesseeName: String,
        LesseeAddress: String,
        ItemCheck: Boolean,
        ItemOther: String,
        PICContact: String,
        PICTel: String
    },
    setup() {
        function exportPDF() {
            try {
                html2pdf(document.getElementById("element-pdfreport"), {
                    margin: [30, 25, 10, 10],
                    jsPDF: { unit: "mm", format: "a4", orientation: "portrait" },
                    mode: { mode: ["aviod-all", "css", "legacy"] },
                    html2canvas: { dpi: 1200, scale: 12 },
                    filename: "reportname" + Date.now() + ".pdf",
                });
            } catch (error) {
                console.log(error);
            }
        }

        return {
            exportPDF,
        };
    },
}


<!--<div class="container mt-2">
    <div>
        <form>
            <button onclick="exportPDF()" class="btn btn-outline-secondary">
                <span class="form-text">Export to PDF</span>
            </button>
        </form>
    </div>
    <hr />
    <div id="element-pdfreport">
        <div class="Printer">
            <div class="detail" style="marginTop: 25px; fontSize: 12px;">
                <div class="detail1" style="marginTop: 4px;">
                    <label style="width: 120px;">วันที่จัดส่ง / Date</label>
                    <label style="width: 200px;"><strong>{{ date = new Date().toLocaleDateString('en-GB', { year: 'numeric', month: 'short', day: 'numeric' }) }}</strong></label>
                </div>
                <div class="detail2" style="marginTop: 4px;">
                    <label style="width: 120px;">ชื่อลูกค้า / Lessee</label>
                    <label style="width: 200px;"><strong>{{ LesseeName }}</strong></label>
                </div>
                <div class="detail3" style="marginTop: 4px;">
                    <label style="width: 120px;">ที่อยู่ลูกค้า / Address</label>
                    <label style="width: 200px;"><strong>{{ LesseeAddress }}</strong></label>
                </div>
            </div>
        </div>
        <div class="Header">
            <div class="header text-center" style="marginTop: 60px; fontSize: 14px;">
                <strong>ใบรายการเอกสารสัญญาเช่า/สัญญาเช่าซื้อ</strong>
            </div>
            <div class="detail" style="marginTop: 30px; fontSize: 12px;">
                <div class="detail1">
                    <label style="width: 120px;">วันที่จัดส่ง / Date</label>
                    <label><strong>{{ date = new Date().toLocaleDateString('en-GB', { year: 'numeric', month: 'short', day: 'numeric' }) }}</strong></label>
                </div>
                <div class="detail2" style="marginTop: 7px;">
                    <label style="width: 100px;">ชื่อลูกค้า / Lessee</label>
                    <label style="width: 300px;"><strong>{{ LesseeName }}</strong></label>
                    <label style="width: 170px;">เลขที่สัญญา / Contract No</label>
                    <label><strong>{{ ContractNo }}</strong></label>
                </div>
            </div>
            <div class="footer" style="marginTop: 30px; fontSize: 12px;">
                <div>บริษัทฯ ขอจัดส่งเอกสารที่ท่านได้ทำสัญญาเช่า / สัญญาเช่าซื้อ โดยมีรายการเอกสารดังนี้.-</div>
                <div style="marginTop: 8px;">Enclosed Please find attached documents for Leasing Agreement or Hire Purchase Agreement as follows.-</div>
            </div>
        </div>
        <div class="Checklist">
            <div class="checkbox" style="marginTop: 45px; fontSize: 12px;">
                <div class="checkboxrow1">
                    <input type="checkbox" id="checkbox1" disabled="true" :checked="ItemCheck[0] == true">
                    <label for="checkbox1" style="marginLeft: 10px; width: 350px;">สัญญาเช่า/เช่าซื้อ (Lease Agreement/Hire Purchase Agreement)</label>
                    <input type="checkbox" id="checkbox2" disabled="true" :checked="ItemCheck[1] == true" style="marginLeft: 10px;">
                    <label for="checkbox2" style="marginLeft: 10px; width: 250px;">ใบรับทรัพย์สิน (Acceptance Receipt)</label>
                </div>
                <div class="checkboxrow2" style="marginTop: 6px;">
                    <input type="checkbox" id="checkbox3" disabled="true" :checked="ItemCheck[2] == true">
                    <label for="checkbox3" style="marginLeft: 10px; width: 350px;">สัญญาซื้อขาย (Sales Agreement)</label>
                    <input type="checkbox" id="checkbox4" disabled="true" :checked="ItemCheck[3] == true" style="marginLeft: 10px;">
                    <label for="checkbox4" style="marginLeft: 10px; width: 250px;">หนังสือค้ำประกัน (Guarantee Documents)</label>
                </div>
                <div class="checkboxrow3" style="marginTop: 6px;">
                    <input type="checkbox" id="checkbox5" disabled="true" :checked="ItemCheck[4] == true">
                    <label for="checkbox5" style="marginLeft: 10px; width: 350px;">คำขอเช่า (Deposit Transfer Form)</label>
                    <input type="checkbox" id="checkbox6" disabled="true" :checked="ItemCheck[5] == true" style="marginLeft: 10px;">
                    <label for="checkbox6" style="marginLeft: 10px; width: 250px;">คำขอเช่าซื้อ (Down Payment Transfer Form)</label>
                </div>
                <div class="checkboxrow4" style="marginTop: 6px;">
                    <input type="checkbox" id="checkbox7" disabled="true" :checked="ItemCheck[6] == true">
                    <label for="checkbox7" style="marginLeft: 10px; width: 350px;">เอกสารแนบ (Attachment)</label>
                    <input type="checkbox" id="checkbox8" disabled="true" :checked="ItemCheck[7] == true" style="marginLeft: 10px;">
                    <label for="checkbox8" style="marginLeft: 10px; width: 250px;">บันทึกข้อตกลงวิธีการชำระราคาทรัพย์สิน</label>
                </div>
                <div class="checkboxrow5" style="marginTop: 6px;">
                    <input type="checkbox" id="checkbox9" disabled="true" :checked="ItemCheck[8] == true">
                    <label for="checkbox9" style="marginLeft: 10px; width: 350px;">ตารางการชำระเงิน (Payment Schedule)</label>
                    <input type="checkbox" id="checkbox10" disabled="true" :checked="ItemCheck[9] == true" style="marginLeft: 10px;">
                    <label for="checkbox10" style="marginLeft: 10px; width: 250px;">บันทึกข้อตกลงต่อท้ายสัญญาเช่า</label>
                </div>
                <div class="checkboxrow6" style="marginTop: 6px;">
                    <input type="checkbox" id="checkbox11" disabled="true" :checked="ItemCheck[10] == true">
                    <label for="checkbox11" style="marginLeft: 10px; width: 350px;">ตารางการตัดบัญชี (Interest Schedule)</label>
                </div>
                <div class="checkboxrow7" style="marginLeft: 40px; marginTop: 30px;">
                    <div class="checkboxother">
                        <input type="checkbox" id="checkbox12" disabled="true" :checked="ItemCheck[11] == true">
                        <label for="checkbox12" style="marginLeft: 25px;">เอกสารอื่น ๆ (Other)</label>
                    </div>
                    <div class="checkboxotherdetail" style="marginLeft: 20px;">
                        <div class="checkboxotherdetail1" style="marginTop: 4px;">
                            <label><strong>A:&nbsp;&nbsp;{{ ItemOther[0] }}</strong></label>
                        </div>
                        <div class="checkboxotherdetail2" style="marginTop: 4px;">
                            <label><strong>B:&nbsp;&nbsp;{{ ItemOther[1] }}</strong></label>
                        </div>
                        <div class="checkboxotherdetail3" style="marginTop: 4px;">
                            <label><strong>C:&nbsp;&nbsp;{{ ItemOther[2] }}</strong></label>
                        </div>
                        <div class="checkboxotherdetail4" style="marginTop: 4px;">
                            <label><strong>D:&nbsp;&nbsp;{{ ItemOther[3] }}</strong></label>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="Footer">
            <div class="footer" style="marginTop: 20px; fontSize: 12px;">
                <div class="footer1_1">
                    <label style="marginLeft: 70px;"><strong>ดังนั้นขอให้ท่านตรวจสอบเอกสารตามรายการข้างต้นให้ครบถ้วน หากได้รับไม่ถูกต้องหรือไม่ครบถ้วน</strong></label>
                </div>
                <div class="footer1_2">
                    <label style="marginLeft: 30px; marginTop: 7px;"><strong>กรุณาแจ้งกลับภายใน 15 วัน นับจากวันที่มีการระบุไว้ในเอกสารฉบับนี้ มิฉะนั้นบริษัทฯ จะไม่รับผิดชอบใด ๆ ทั้งสิ้น</strong></label>
                </div>
                <div class="footer1_1">
                    <label style="marginLeft: 70px; marginTop: 15px;">Please check above documents for correctness and completeness. If there are any mistake,Please notify us</label>
                </div>
                <div class="footer1_2">
                    <label style="marginLeft: 30px; marginTop: 7px;">within 15 days from this letter dated.</label>
                </div>
            </div>
        </div>
        <div class="Contact">
            <div class="contract" style="marginTop: 80px; fontSize: 12px;">
                <div class="contract1">
                    <label style="width: 70px;">ติดต่อ</label>
                    <label style="width: 150px;"><strong>{{ PICContact }}</strong></label>
                </div>
                <div class="contract2" style="marginTop: 7px;">
                    <label style="width: 70px;">โทร</label>
                    <label style="width: 300px;"><strong>{{ PICTel }}</strong></label>
                </div>
            </div>
        </div>
    </div>
</div>
-->




<script>
import html2pdf from 'html2pdf.js';

export default {
    props: {
        ContractNo: [String, Number],
        LesseeName: String,
        LesseeAddress: String,
        ItemCheck: Boolean,
        ItemOther: String,
        PICContact: String,
        PICTel: String
    },
    setup() {
        function exportPDF() {
            try {
                html2pdf(document.getElementById("element-pdfreport"), {
                    margin: [30, 25, 10, 10],
                    jsPDF: { unit: "mm", format: "a4", orientation: "portrait" },
                    mode: { mode: ["aviod-all", "css", "legacy"] },
                    html2canvas: { dpi: 1200, scale: 12 },
                    filename: "reportname" + Date.now() + ".pdf",
                });
            } catch (error) {
                console.log(error);
            }
        }

        return {
            exportPDF,
        };
    },
}

</script>

<template>
    <div class="container mt-2">
        <div>
            <form>
                <button @click="exportPDF" class="btn btn-outline-secondary">
                    <span class="form-text">Export to PDF</span>
                </button>
            </form>
        </div>
        <hr />
        <div id="element-pdfreport">
            <div class="Printer">
                <div class="detail" :style="{ marginTop: '25px', fontSize: '12px' }">
                    <div class="detail1" style="margin-top: 4px;">
                        <label style="width: 120px;">วันที่จัดส่ง / Date</label>
                        <label style="width: 200px;"><strong>{{ date = new Date().toLocaleDateString('en-GB', { year: 'numeric', month: 'short', day: 'numeric' }) }}</strong></label>
                    </div>
                    <div class="detail2" style="margin-top: 4px;">
                        <label style="width: 120px;">ชื่อลูกค้า / Lessee</label>
                        <label style="width: 200px;"><strong>{{ LesseeName }}</strong></label>
                    </div>
                    <div class="detail3" style="margin-top: 4px;">
                        <label style="width: 120px;">ที่อยู่ลูกค้า / Address</label>
                        <label style="width: 200px;"><strong>{{ LesseeAddress }}</strong></label>
                    </div>
                </div>
            </div>
            <div class="Header">
                <div class="header text-center" :style="{ marginTop: '60px', fontSize: '14px' }">
                    <strong>ใบรายการเอกสารสัญญาเช่า/สัญญาเช่าซื้อ</strong>
                </div>
                <div class="detail" :style="{ marginTop: '30px', fontSize: '12px' }">
                    <div class="detail1">
                        <label style="width: 120px;">วันที่จัดส่ง / Date</label>
                        <label><strong>{{ date = new Date().toLocaleDateString('en-GB', { year: 'numeric', month: 'short', day: 'numeric' }) }}</strong></label>
                    </div>
                    <div class="detail2" style="margin-top: 7px;">
                        <label style="width: 100px;">ชื่อลูกค้า / Lessee</label>
                        <label style="width: 300px;"><strong>{{ LesseeName }}</strong></label>
                        <label style="width: 170px;">เลขที่สัญญา / Contract No</label>
                        <label><strong>{{ ContractNo }}</strong></label>
                    </div>
                </div>
                <div class="footer" :style="{ marginTop: '30px', fontSize: '12px' }">
                    <div>บริษัทฯ ขอจัดส่งเอกสารที่ท่านได้ทำสัญญาเช่า / สัญญาเช่าซื้อ โดยมีรายการเอกสารดังนี้.-</div>
                    <div style="margin-top: 8px;">Enclosed Please find attached documents for Leasing Agreement or Hire Purchase Agreement as follows.-</div>
                </div>
            </div>
            <div class="Checklist">
                <div class="checkbox" :style="{ marginTop: '45px', fontSize: '12px' }">
                    <div class="checkboxrow1">
                        <input type="checkbox" id="checkbox1" disabled="true" :checked="ItemCheck[0] == true">
                        <label for="checkbox1" :style="{ marginLeft: '10px', width: '350px' }">สัญญาเช่า/เช่าซื้อ (Lease Agreement/Hire Purchase Agreement)</label>
                        <input type="checkbox" id="checkbox2" disabled="true" :checked="ItemCheck[1] == true" style="margin-left: 10px;">
                        <label for="checkbox2" :style="{ marginLeft: '10px', width: '250px' }">ใบรับทรัพย์สิน (Acceptance Receipt)</label>
                    </div>
                    <div class="checkboxrow2" style="margin-top: 6px;">
                        <input type="checkbox" id="checkbox3" disabled="true" :checked="ItemCheck[2] == true">
                        <label for="checkbox3" :style="{ marginLeft: '10px', width: '350px' }">สัญญาซื้อขาย (Sales Agreement)</label>
                        <input type="checkbox" id="checkbox4" disabled="true" :checked="ItemCheck[3] == true" style="margin-left: 10px;">
                        <label for="checkbox4" :style="{ marginLeft: '10px', width: '250px' }">หนังสือค้ำประกัน (Guarantee Documents)</label>
                    </div>
                    <div class="checkboxrow3" style="margin-top: 6px;">
                        <input type="checkbox" id="checkbox5" disabled="true" :checked="ItemCheck[4] == true">
                        <label for="checkbox5" :style="{ marginLeft: '10px', width: '350px' }">คำขอเช่า (Deposit Transfer Form)</label>
                        <input type="checkbox" id="checkbox6" disabled="true" :checked="ItemCheck[5] == true" style="margin-left: 10px;">
                        <label for="checkbox6" :style="{ marginLeft: '10px', width: '250px' }">คำขอเช่าซื้อ (Down Payment Transfer Form)</label>
                    </div>
                    <div class="checkboxrow4" style="margin-top: 6px;">
                        <input type="checkbox" id="checkbox7" disabled="true" :checked="ItemCheck[6] == true">
                        <label for="checkbox7" :style="{ marginLeft: '10px', width: '350px' }">เอกสารแนบ (Attachment)</label>
                        <input type="checkbox" id="checkbox8" disabled="true" :checked="ItemCheck[7] == true" style="margin-left: 10px;">
                        <label for="checkbox8" :style="{ marginLeft: '10px', width: '250px' }">บันทึกข้อตกลงวิธีการชำระราคาทรัพย์สิน</label>
                    </div>
                    <div class="checkboxrow5" style="margin-top: 6px;">
                        <input type="checkbox" id="checkbox9" disabled="true" :checked="ItemCheck[8] == true">
                        <label for="checkbox9" :style="{ marginLeft: '10px', width: '350px' }">ตารางการชำระเงิน (Payment Schedule)</label>
                        <input type="checkbox" id="checkbox10" disabled="true" :checked="ItemCheck[9] == true" style="margin-left: 10px;">
                        <label for="checkbox10" :style="{ marginLeft: '10px', width: '250px' }">บันทึกข้อตกลงต่อท้ายสัญญาเช่า</label>
                    </div>
                    <div class="checkboxrow6" style="margin-top: 6px;">
                        <input type="checkbox" id="checkbox11" disabled="true" :checked="ItemCheck[10] == true">
                        <label for="checkbox11" :style="{ marginLeft: '10px', width: '350px' }">ตารางการตัดบัญชี (Interest Schedule)</label>
                    </div>
                    <div class="checkboxrow7" :style="{ marginLeft: '40px', marginTop: '30px' }">
                        <div class="checkboxother">
                            <input type="checkbox" id="checkbox12" disabled="true" :checked="ItemCheck[11] == true">
                            <label for="checkbox12" style="margin-left: 25px;">เอกสารอื่น ๆ (Other)</label>
                        </div>
                        <div class="checkboxotherdetail" style="margin-left: 20px;">
                            <div class="checkboxotherdetail1" style="margin-top: 4px;">
                                <label><strong>A:&nbsp;&nbsp;{{ ItemOther[0] }}</strong></label>
                            </div>
                            <div class="checkboxotherdetail2" style="margin-top: 4px;">
                                <label><strong>B:&nbsp;&nbsp;{{ ItemOther[1] }}</strong></label>
                            </div>
                            <div class="checkboxotherdetail3" style="margin-top: 4px;">
                                <label><strong>C:&nbsp;&nbsp;{{ ItemOther[2] }}</strong></label>
                            </div>
                            <div class="checkboxotherdetail4" style="margin-top: 4px;">
                                <label><strong>D:&nbsp;&nbsp;{{ ItemOther[3] }}</strong></label>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="Footer">
                <div class="footer"  :style="{ marginTop: '20px', fontSize: '12px' }">
                    <div class="footer1_1">
                        <label :style="{ marginLeft: '70px' }"><strong>ดังนั้นขอให้ท่านตรวจสอบเอกสารตามรายการข้างต้นให้ครบถ้วน หากได้รับไม่ถูกต้องหรือไม่ครบถ้วน</strong></label>
                    </div>
                    <div class="footer1_2">
                        <label :style="{ marginLeft: '30px', marginTop: '7px' }"><strong>กรุณาแจ้งกลับภายใน 15 วัน นับจากวันที่มีการระบุไว้ในเอกสารฉบับนี้ มิฉะนั้นบริษัทฯ จะไม่รับผิดชอบใด ๆ ทั้งสิ้น</strong></label>
                    </div>
                    <div class="footer1_1">
                        <label :style="{ marginLeft: '70px', marginTop: '15px'  }">Please check above documents for correctness and completeness. If there are any mistake,Please notify us</label>
                    </div>
                    <div class="footer1_2">
                        <label :style="{ marginLeft: '30px', marginTop: '7px'  }">within 15 days from this letter dated.</label>
                    </div>
                </div>
            </div>
            <div class="Contact">
                <div class="contract" :style="{ marginTop: '80px', fontSize: '12px' }">
                    <div class="contract1">
                        <label style="width: 70px;">ติดต่อ</label>
                        <label style="width: 150px;"><strong>{{ PICContact }}</strong></label>
                    </div>
                    <div class="contract2" style="margin-top: 7px;">
                        <label style="width: 70px;">โทร</label>
                        <label style="width: 300px;"><strong>{{ PICTel }}</strong></label>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template> 

