---
layout: default
title: Page 2 Example (Variable Check Grader)
---

Construct a program that outputs the cumulative sum of its input.

<div id="sortableTrash" class="sortable-code"></div> 
<div id="sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="feedbackLink" value="Get Feedback" type="button" /> 
    <input id="newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "def cumulative(x):
\n" +
    "    out = 0
\n" +
    "    for i in range(1,$$toggle::x::x+1$$):
\n" +
    "        out = out + $$toggle::i::x::1::out$$
\n" +
    "    return out";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.UnitTestGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "python3": true,
    "trashId": "sortableTrash",
    "unittest_code_prepend": "",
    "unittests": "import unittestparson\nclass myTests(unittestparson.unittest):\n  def test_0(self):\n    self.assertEqual(cumulative(1),1,)\n  def test_1(self):\n    self.assertEqual(cumulative(2),3,)\n  def test_2(self):\n    self.assertEqual(cumulative(8),36,)\n_test_result = myTests().main()"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

[Next](./example2.html)
