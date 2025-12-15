

function Atleta(nome, idade, peso, altura, notas) {
  this.nome = nome;
  this.idade = idade;
  this.peso = peso;
  this.altura = altura;
  this.notas = notas; }

Atleta.prototype.calculaCategoria = function () {
  let idade = this.idade;
  if (idade >= 9 && idade <= 11) {
    return 'Infantil';
  } else if (idade === 12 || idade === 13) {
    return 'Juvenil';
  } else if (idade === 14 || idade === 15) {
    return 'Intermediário';
  } else if (idade >= 16 && idade <= 30) {
    return 'Adulto';
  } else {
    return 'Sem categoria';
  }
};

Atleta.prototype.calculaIMC = function () {
  let imc = this.peso / (this.altura * this.altura);
  return imc;
};

Atleta.prototype.calculaMediaValida = function () {
  let notas = this.notas.slice();
  notas.sort(function (a, b) { return a - b; });

  let notasComputadas = notas.slice(1, 4);
  let soma = 0;
  notasComputadas.forEach(function (n) {
    soma += n;
  });

  let media = soma / notasComputadas.length;
  return media;
};

Atleta.prototype.obtemNomeAtleta = function () { return this.nome; };
Atleta.prototype.obtemIdadeAtleta = function () { return this.idade; };
Atleta.prototype.obtemPesoAtleta = function () { return this.peso; };
Atleta.prototype.obtemAlturaAtleta = function () { return this.altura; };
Atleta.prototype.obtemNotasAtleta = function () { return this.notas.join(','); };
Atleta.prototype.obtemCategoria = function () { return this.calculaCategoria(); };
Atleta.prototype.obtemIMC = function () { return this.calculaIMC(); };
Atleta.prototype.obtemMediaValida = function () { return this.calculaMediaValida(); };

let atleta = new Atleta(
  "Cesar Abascal",
  30,
  80,
  1.7,
  [10, 9.34, 8.42, 10, 7.88]
);

console.log('Nome: ' + atleta.obtemNomeAtleta());
console.log('Idade: ' + atleta.obtemIdadeAtleta());
console.log('Peso: ' + atleta.obtemPesoAtleta());
console.log('Altura: ' + atleta.obtemAlturaAtleta());
console.log('Notas: ' + atleta.obtemNotasAtleta());
console.log('Categoria: ' + atleta.obtemCategoria());
console.log('IMC: ' + atleta.obtemIMC());
console.log('Média válida: ' + atleta.obtemMediaValida());


