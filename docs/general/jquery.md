## add click event for dynamically generated elements

```js
// generate dynamically elements
$('#assign-modal-add').click(function(e) {
    var userID = $('#assign-modal-userIDInput').val();
    $('#assign-modal-userIDList').append('<li class="list-group-item">' + userID + '<span class="glyphicon glyphicon-remove assign-modal-userID-remove" aria-hidden="true"></span></li>');
    $('#assign-modal-userIDInput').val("");
});
// this one will not working anymore
$('.assign-modal-userID-remove').click(function(e) {
    $(this).parent().remove();
});

// using this instead
$(document).on('click', '.assign-modal-userID-remove', function(e) {
    $(this).parent().remove();
});
