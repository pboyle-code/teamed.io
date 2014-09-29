---
layout: landing
title: "Cost Calculator"
permalink: /calculator.html
description:
  How much does a normal project cost with Teamed.io? This
  calculator will give you a ballpark estimate
keywords:
  - cost of software
  - how much software costs
  - calculate cost of software
  - rough order of magnitude
  - estimate software cost
---

Give us the size of the software you need to develop and
we'll calculate its cost, if you do it with us:

KLoC: <input id="kloc" name="kloc" value="20"/>

<span id="error" style="display:none;color:red"></span>

<style type="text/css">
.mm {
  text-align: right;
}
</style>
<table>
  <tr><td></td><td>Team players (peak time)</td><td class="mm" id="coders"></td></tr>
  <tr><td>T</td><td>Completed tasks</td><td class="mm" id="t"></td></tr>
  <tr><td>PR</td><td>Pull requests</td><td class="mm" id="pr"></td></tr>
  <tr><td>R</td><td>Average hourly rate</td><td class="mm" id="r"></td></tr>
  <tr><td>P</td><td>Paid to players</td><td class="mm" id="p"></td></tr>
  <tr><td>TM</td><td>Technical margin (69% of P)</td><td class="mm" id="tm"></td></tr>
  <tr><td>PM</td><td>Management fee ($19 per T and PR)</td><td class="mm" id="pm"></td></tr>
  <tr><td>MF</td><td>Merge fee ($49 per PR)</td><td class="mm" id="mf"></td></tr>
  <tr><td></td><td>Total (P+TM+PM+MF)</td><td class="mm" id="total"></td></tr>
</table>

These numbers are very preliminary. For a more precise and
accurate estimate, email us.

<script type="text/javascript">
function dollars(val) {
  return '$' + val;
}
$(document).ready(
  function() {
    $('#kloc').keyup(
      function () {
        var kloc = $(this).val(), $error = $('#error');
        if ($.isNumeric(kloc) && kloc > 5 && kloc < 1000) {
          var coders = Math.round(kloc / 50),
            t = coders * 50,
            pr = Math.round(t * 1.5),
            r = 27,
            p = (t + pr) * r,
            tm = Math.round(0.69 * p),
            pm = 19 * (t + pr),
            mf = 49 * pr;
          $error.hide();
          $('#coders').text(coders);
          $('#t').text(t);
          $('#pr').text(pr);
          $('#r').text(dollars(r));
          $('#p').text(dollars(p));
          $('#tm').text(dollars(tm));
          $('#pm').text(dollars(pm));
          $('#mf').text(dollars(mf));
          $('#total').text(dollars(p + tm + pm + mf));
        } else {
          $error.text('must be an integer, in 5..1000 range').show();
          $('.mm').text('');
        }
      }
    );
  }
);
</script>
