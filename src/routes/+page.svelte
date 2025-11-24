<script type="javascript">
    // Placeholder for future script logic
    let task = $state([]);
    let newtask = $state("");

    function addTask() {
        // Logic to add a new task
        task = [...task, { id: task.length + 1, text: newtask, completed: false }];
        newtask = "";
    }

    function editTask(index, newText) {
        // Logic to edit a task
        task[index].text = newText;
        task = [...task];
    }

    function deleteTask(index) {
        // Logic to delete a task
        task = task.filter((_, i) => i !== index);
    }

    function toggleCompletion(index) {
        // Logic to toggle task completion
        task[index].completed = !task[index].completed;
        task = [...task];
    }
</script>

<div class="container" >
    <h1>Todo List</h1>
<form>
    <input type="text" bind:value={newtask} placeholder="Add a new task" />
    <button type="submit" on:click|preventDefault={addTask}>+</button>
    
</form>
    <ul>
        {#each task as { id, text, completed }, index}
         {#if completed}
            <li> <input type="checkbox" checked on:change={() => toggleCompletion(index)} /> <span style="text-decoration: line-through;">{id} {text} </span> <button on:click={() => editTask(index, prompt("Edit task", text))}>Edit</button> <button on:click={() => deleteTask(index)}>Delete</button></li>
         {:else}
                <li> <input type="checkbox"  on:change={() => toggleCompletion(index)} /> {id} {text}  <button on:click={() => editTask(index, prompt("Edit task", text))}>Edit</button> <button on:click={() => deleteTask(index)}>Delete</button></li>
        {/if}
        {/each}
    </ul>
</div>


<style>
    h1 {
        text-align: center;
    }
    form {
        display: flex;
        justify-content: center;
        margin-bottom: 20px;
    }
    form > input {
        width: 200px;
        padding: 10px;
        margin-right: 10px;
    }
    button {
        padding: 10px 15px;
        cursor: pointer;
        background-color: #007BFF;
        color: #fff;
        border: none;
        border-radius: 5px;
    }
    li > button:last-child {
        background-color: #DC3545;
    }
    ul {
        list-style-type: none;
        display: flex;
        flex-direction: column;
        padding: 0;
        gap: 10px;
    }
    li {
        display: flex;
        gap: 10px;
        padding: 15px;
        align-items: center;
        justify-content: center;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    }
    .container {
        max-width: 400px;
        margin: 0 auto;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 5px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }   
</style>