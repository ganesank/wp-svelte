<script>
  import { userList } from "../store";
  export let author;
  let name = "";
  let allUsers;
  const unsubscribe = userList.subscribe((value) => {
    allUsers = value;
  });
  if (allUsers && allUsers.length > 0) {
    let obj = allUsers.find((o) => o.id === author);
    if (obj && obj.name) {
      name = obj.name;
    }
  }
</script>

<span>{name}</span>
