---
layout: post
title:  "Percebendo problemas através de narrativas"
date:   2017-03-03 23:08:00 -0300
tags:
- desenvolvimento-projetos
---
<button role="button" name="randomizer" data-collection="places">Lugar</button>
<button role="button" name="randomizer" data-collection="characteristics">Característica</button>
<button role="button" name="randomizer" data-collection="factors">Fator</button>

<script>
    (function() {
        var places = [
            'sítio', 'campo', 'escola', 'cidade',
            'hospital', 'montanha', 'viagem', 'avião',
            'navio', 'carro', 'apartamento', 'casa',
            'rua', 'festa de rua', 'perto do colégio',
            'faculdade', 'república', 'hotel', 'parque',
            'praça', 'ônibus', 'loja', 'restaurante', 'praia',
            'evento', 'academia', 'rodovia', 'empresa', 'show',
            'balada', 'estádio', 'clube', 'floresta', 'centro da cidade',
            'perdido na cidade', 'pizzaria', 'ponto de ônibus',
            'banheiro', 'cabeleireiro', 'piscina',
        ];
        
        var characteristics = [
            'alto', 'braço quebrado', 'baixo', 'pé quebrado',
            'idoso', 'jovem', 'criança', 'professor', 'enfermeiro',
            'programador', 'mecânico', 'cozinheiro', 'pai / mãe',
            'fazendeiro', 'dançarino', 'músico', 'voluntário',
            'artista', 'ator', 'cientista', 'pesquisador', 'médico',
            'produtor de conteúdo', 'gerente', 'engenheiro', 'ansioso',
            'autista', 'doença de Parkinson', 'pedreiro', 'arquiteto',
            'inserguro', 'medroso', 'pobre', 'viajante', 'tímido',
            'designer', 'editor de vídeo', 'farmacêutico', 'secretário',
            'psicólogo', 'organizado', 'nervoso', 'bom leitor', 'mal leitor',
            'dificuldade em estudar', 'advogado', 'surdo', 'cego',
            'baixa visão', 'paraplégico', 'deficiência cognitiva',
            'baladeiro', 'apaixonado por animais', 'morador de favela',
            'pele sensível', 'friento', 'viciado em redes sociais',
            'bêbado', 'bebê',
        ];
        
        var factors = [
            'acidente de carro', 'tropeçar', 'problema de saúde',
            'machuado', 'prova chegando', 'conheceu alguém', 'dificuldade em aprender',
            'precisa tomar uma decisão', 'prova chegando', 'dia muito ocupado',
            'perdeu o ônibus', 'chuva forte', 'sol forte', 'foi roubado',
            'quer encontrar uma pessoa', 'quer comprar algo', 'stalkeou alguém',
            'encontrou algo de alguém', 'ficou gripado', 'começou a morar sozinho',
            ''
        ];
        
        function random(collection) {
            var index = Math.floor(Math.random() * collection.length);
            return collection[index];
        }
        
        var randomizables = {
            places: places,
            characteristics: characteristics,
            factors: factors,
        };
        
        document.getElementsByName('randomizer').forEach(function(element) {
            var collection = element.getAttribute('data-collection');
            element.addEventListener('click', function() {
                alert(random(randomizables[collection]));
            });
        });
    })();
</script>