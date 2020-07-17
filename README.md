$(document).ready(function () {

  $('#form').submit(function (event) {
    var formData = $('#form').serialize();
    let $form = $('#form')
    $.ajax({
      url: $form.attr('action'),
      data: formData,
      type: "POST",
      dataType: "xml",
      statusCode: {
        0: function () {
          //送信に成功したとき
          $form.slideUp()
          $("送信メッセージのＩＤ").slideDown();
          // $("サブミットクラス").fadeOut();
          //window.location.href = "thanks.html";
        },
        200: function () {
          $form.slideUp()
          $("送信失敗のクラス").slideDown();
        }
      }
    });
    event.preventDefault();
  });

});

let $submit = $('ボタンのＩＤ')
$('#form input , #form textarea').on('change' , function(){
  if(
    $('#form input[type="text"]').val() !== "" &&
    $('#form input[type="email"]').val() !== "" &&
    $('#form input[name="entry.2102378070"]').prop('checked') === true
  ){
    $submit.prop('disabled' , false)
    $submit.addClass('-active')
  }else{
    $submit.prop('disabled' , true)
    $submit.removeClass('-active')
  }

})
