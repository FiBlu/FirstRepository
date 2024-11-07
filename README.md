# Мій перший репозиторій
## Знизу я написав код
#### Це рандомайзер занять
*У ньому є **все***
###Наприклад:
* Пограти з друзями у футбол
* Навчитися грати на музичному інструменті
  * Відкрити для себе новий гурт
##### Та дуже багато занять
### *Нижче JS код цього рандомайзера*
```javascript

let types = ["education", "recreational", "social", "diy", "charity", "cooking", "relaxation", "music", "busywork"];

$.each(types, (index, type) => {
    $('#types').append(`
    <label for="${type}">${type.toUpperCase()}:</label>
    <input type="radio" id="${type}" value="${type}" name="type">    
    `)
});
$('#rnd').click(function (){
    let params = $("#filter").serialize();

    $.ajax(`https://bored.api.lewagon.com/api/activity/?${params}`, {
        dataType: 'json', 
        success: (result) => {
            $('#result').html(`
            <h2>Activity: ${result.activity}</h2>
            <h2>Price: ${result.price}</h2>    
            <h2>Type: ${result.type}</h2>    
            `)
        },
        error: (xhr) => {
            $('#result').html(`
            <h2>Error: ${xhr.statusText}</h2>
            `)
        }
    });
});

```
