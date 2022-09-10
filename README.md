module.exports = async function (context, req) {
}

//Função calcula valor a mais ou a menos na conta após a operacao
FLucroBruto = () => {
    return (CapitalFinal - CapitalInicial)
}

//Função Calcula o valor da taxa aplicada
fValorTaxa =() =>{
    return (LucroBruto)*(TaxadaCorretora/100)
}

//Verifica se o usuário obteve lucro ou prejuizo
fLucro = () => {
    return LucroBruto - ValorTaxa
}
fClasificacao=() => {
    if ( CapitaliFinal < CapitalInicial) {
        return 'Voce esta com saldo negativo esta semana';
    } else if (CapitaliFinal = CapitalInicial) {
        return 'Voce esta sem margem de lucro esta semana';
    } else {(CapitaliFinal > CapitalInicial)
        return 'O seu Lucro esta semana foi de  ${Lucro}';
    }
    };

module.exports = async function (context, req) {
    let CapitalInicial = Number(req.query.CapitalInicial);
    let TaxadaCorretora = Number(req.query.TaxadaCorretora);
    let CapitalFinal = Number(req.query.CapitalFinal);


    if (isNaN(CapitalInicial) || isNaN(CapitalFinal) || isNAN(TaxadaCorretora)) {
        return context.res.status(400).send('Formato de dados incorretos, o Capital Inicial, Capital Final e Taxa da Corretoora aceitam somente numeros.');
    }

    let Valor= fValorTaxa((LucroBruto)*(TaxadaCorretora/100));
    let LucroBruto = FLucroBruto(CapitalFinal - CapitalInicial);
    let Lucro = fLucro (LucroBruto - ValorTaxa);
    


    context.res.json({
        CapitalInicial: CapitalInicial, 
        TaxadaCorretora:TaxadaCorretora, 
        CapitalFinal: CapitalFinal
        Lucro:Lucro,
        LucroBruto: LucroBruto,
        Classificacao: Classificacao,
    });
}
