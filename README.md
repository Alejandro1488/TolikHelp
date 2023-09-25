# TolikHelp

Пример кода для прошлого экза отсюда можешь потягать нужные вещи
шаги для 1 задания:
выгрузить данные из фикстуры пример можешь посмотреть в коде ниже. дальше нужно посчитать количество строчек которые получлись метод size(мб параметр не помню) выведет количество как раз и выполнить условие вывода


задание 2:
выгрузить данные из фикстуры проходимя по элементо по массиву данных напрмер for опять же код ниже пример. все имена барбершопов по строчке когда итерируешь это массив и делаешь массив[нномер элемента -  1] добавляешь в новый массив после его сортируешь  sort по алфавиту и выводишь

задание 3:
выгружаешь данные из фикстуры начинаешь собирать в новый массив все существующие рейтинги подряд после на массиве вызываешь методы min и max и выводишь по условию задания

function capitalizeFirstLetter(str) {
    return str.charAt(0).toUpperCase() + str.slice(1);
  }
  
  function getName(data) {
    let maxdist = 0;
    let name = '';
    data.forEach((row) => {
      const largest = parseFloat(row[4]);
      if (largest > maxdist) {
        maxdist = largest;
        name = row[2];
      }
    });
    return `Largest hp: ${name}`;
  }
  
  function getDamage(data) {
    let damage = 0;
    let name = '';
    const result = [];
    data.forEach((row) => {
      damage = row[3].split('-');
      name = row[2];
      if (damage.length > 1) {
        damage = (parseFloat(damage[0]) + parseFloat(damage[1])) / 2;
      } else {
        damage = damage[0];
      }
      result.push(`${name}: ${damage}`);
    });
    return `Average damage: ${result.join(', ')}`;
  }
  
  function calculateDamage(damageRange) {
    let damage = damageRange.split('-');
    if (damage.length > 1) {
      damage = (parseFloat(damage[0]) + parseFloat(damage[1])) / 2;
    } else {
      damage = damage[0];
    }
    return damage;
  }
  
  function getPowerEntity(data) {
    const level7Creatures = data.filter((creature) => creature[0] === '7');
    let strongestCreature = null;
    let minAttacks = Infinity;
    for (const creature of level7Creatures) {
      const name = creature[2];
      const damageRange = creature[3];
      const damage = calculateDamage(damageRange);
      for (const creature1 of level7Creatures) {
        const name1 = creature1[2];
        if (name !== name1) {
          const health1 = creature1[4];
          if (minAttacks > health1 / damage) {
            minAttacks = health1 / damage;
            strongestCreature = name;
          }
        }
      }
    }
  
    return `Strongest creature: ${strongestCreature}`;
  }
  
  const solution = (content) => {
    const data = content.split('\n').slice(1).map((line) => line.split(' '));
    console.log(`Count: ${data.length}`);
  
    const costles = new Set();
    data.forEach((row) => {
      costles.add(capitalizeFirstLetter(row[1].toLowerCase()));
    });
    console.log(`Castles: ${Array.from(costles).sort().join(', ')}`);
  
    const name = getName(data);
    console.log(name);
  
    const damage = getDamage(data);
    console.log(damage);
  
    const powerEntity = getPowerEntity(data);
    console.log(powerEntity);
  };
  
  export default solution;`


  
