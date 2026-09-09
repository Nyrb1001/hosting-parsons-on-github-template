---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Multiple Parson's Problems on One Page
---
# Parsons Practice

## Parsons 1 (Line Based Grader)
Arrange the blocks such that the code will output the cumulative sum of its input. For example, an input of five would yield an output of 5+4+3+2+1 = **15**
<div id="itter-sortableTrash" class="sortable-code"></div> 
<div id="itter-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="itter-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="itter-newInstanceLink" value="Reset Problem" type="button" /> 
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
    "sortableId": "itter-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.UnitTestGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "python3": true,
    "trashId": "itter-sortableTrash",
    "unittest_code_prepend": "",
    "unittests": "import unittestparson\nclass myTests(unittestparson.unittest):\n  def test_0(self):\n    self.assertEqual(cumulative(1),1,)\n  def test_1(self):\n    self.assertEqual(cumulative(2),3,)\n  def test_2(self):\n    self.assertEqual(cumulative(8),36,)\n_test_result = myTests().main()"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#itter-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#itter-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>
### Implementation Notes

When you host multiple Parson's problems on a single markdown page, you need to add a unique prefix. You can easily do this in the Codio generator by typing a unique prefix into the "Prefix" textbox and pressing Enter/Return. Then you can simply copy-paste like normal.

If want each problem to be it's own page, you can use relative path links at the bottom of each of your markdown pages as seen below. If you want students to be able to return to previous problems in this format, consider adding previous links or link to a table of contents like page.

### Example Next Link
[Next](./parsons/example1.html)
