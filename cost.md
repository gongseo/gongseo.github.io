---
layout: default
title: 비용
permalink: /cost/
---

# 여행 비용 정리

각 칸에 금액(원)을 입력하면, 아래 표에서 **총합이 자동 계산**됩니다.  
(페이지를 새로고침하면 값은 초기화돼요 – 서버 저장은 안 됩니다.)

<table class="cost-table" id="cost-table">
  <thead>
    <tr>
      <th>항목</th>
      <th>설명</th>
      <th>금액 (₩)</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>항공</td>
      <td>인천 ↔ 타오위안</td>
      <td>
        <input type="number" class="cost-input" min="0" step="1000" value="350000">
      </td>
    </tr>

    <tr>
      <td>교통</td>
      <td>MRT / 버스 / 도시 간 이동</td>
      <td>
        <input type="number" class="cost-input" min="0" step="1000" value="50000">
      </td>
    </tr>

    <tr>
      <td>숙소</td>
      <td>타이중 2박 + 타이베이 3박</td>
      <td>
        <input type="number" class="cost-input" min="0" step="1000" value="300000">
      </td>
    </tr>

    <tr>
      <td>식비</td>
      <td>5일 (하루 평균)</td>
      <td>
        <input type="number" class="cost-input" min="0" step="1000" value="150000">
      </td>
    </tr>

    <tr>
      <td>기타</td>
      <td>입장료, 기념품 등</td>
      <td>
        <input type="number" class="cost-input" min="0" step="1000" value="80000">
      </td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td colspan="2"><strong>총합</strong></td>
      <td><strong><span id="cost-total">0</span> 원</strong></td>
    </tr>
  </tfoot>
</table>

<script>
  function updateCostTotal() {
    const inputs = document.querySelectorAll('.cost-input');
    let sum = 0;

    inputs.forEach(function (input) {
      const value = parseInt(input.value, 10);
      if (!isNaN(value)) {
        sum += value;
      }
    });

    const totalSpan = document.getElementById('cost-total');
    if (totalSpan) {
      totalSpan.textContent = sum.toLocaleString('ko-KR');
    }
  }

  document.addEventListener('input', function (event) {
    if (event.target.classList.contains('cost-input')) {
      updateCostTotal();
    }
  });

  document.addEventListener('DOMContentLoaded', updateCostTotal);
</script>
