let dadosParticipantes = [];

function checkInDistribuidor() {
    const codigo = document.getElementById('codigo').value;
    // Aqui você deve validar o código (para simplicidade, vamos ignorar isso)
    const nome = "Distribuidor " + codigo; // Simulação do nome
    const posicao = "Distribuidor"; // Simulação da posição
    const dataHora = new Date().toLocaleString();
    
    dadosParticipantes.push({ codigo, nome, posicao, dataHora });
    mostrarConfirmacao(`Check-in realizado para ${nome} (${posicao})`);
}

function checkInConvidado() {
    const nome = document.getElementById('nome').value;
    const telefone = document.getElementById('telefone').value;
    const email = document.getElementById('email').value;
    const dataHora = new Date().toLocaleString();

    dadosParticipantes.push({ codigo: 'N/A', nome, telefone, email, dataHora });
    mostrarConfirmacao(`Check-in realizado para ${nome}`);
}

function mostrarConfirmacao(mensagem) {
    document.getElementById('check-in-form').style.display = 'none';
    document.getElementById('guest-form').style.display = 'none';
    document.getElementById('confirmation').style.display = 'block';
    document.getElementById('confirmacao-mensagem').innerText = mensagem;
}

function exportarDados() {
    const csvContent = "data:text/csv;charset=utf-8,"
        + dadosParticipantes.map(e => Object.values(e).join(",")).join("\n");
    
    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", "participantes.csv");
    document.body.appendChild(link);
    link.click();
}
