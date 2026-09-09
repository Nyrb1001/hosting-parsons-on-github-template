---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Multiple Parson's Problems on One Page
---
# Parsons Practice

## Parsons 1 (Line Based Grader)
Arrange the blocks such that the code will output the cumulative sum of its input. For example, an input of five would yield an output of 5+4+3+2+1 = 15


<div id="test1-sortableTrash" class="sortable-code"></div> 
<div id="test1-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="test1-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="test1-newInstanceLink" value="Reset Problem" type="button" /> 
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
    "sortableId": "test1-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.UnitTestGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "python3": true,
    "trashId": "test1-sortableTrash",
    "unittest_code_prepend": "",
    "unittests": "import unittestparson\nclass myTests(unittestparson.unittest):\n  def test_0(self):\n    self.assertEqual(cumulative(1),1,)\n  def test_1(self):\n    self.assertEqual(cumulative(2),3,)\n  def test_2(self):\n    self.assertEqual(cumulative(8),36,)\n_test_result = myTests().main()"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#test1-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#test1-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>
