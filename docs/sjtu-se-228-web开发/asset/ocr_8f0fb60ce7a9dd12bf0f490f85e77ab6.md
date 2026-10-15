```
• index.html
<script type="text/javascript" src="jquery-2.1.0.js"></script>
<script type="text/javascript" src="jquery-easyui-1.3.5/jquery.easyui.min.js"></script>

<script type="text/javascript">
    var url;
    function newUser(){
        $('#dlg').dialog('open').dialog('setTitle','New User');
        $('#fm').form('clear');
        url = 'save_user.php';
    }

    function editUser(){
        var row = $('#dg').datagrid('getSelected');
        if (row){
            $('#dlg').dialog('open').dialog('setTitle','Edit User');
            $('#fm').form('load',row);
            url = 'update_user.php?id='+row.id;
        }
    }

```