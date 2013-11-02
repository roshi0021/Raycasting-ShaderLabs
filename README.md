Raycasting-ShaderLabs
=====================

Trabalho 2 - CG 

Neste trabalho, o aluno deverá realizar a visualização de terreno 3d a partir de diversas texturas usando a IDE de programação de shaders: Shader Labs. Ele fará isso através da programação de diferentes shaders GLSL: vertex e frag.
Para tal, deve-se usar o modelo “cubo” do Shaderlabs. Dessa maneira as paredes do cubo vão servir de suporte para que o algoritmo de raycast no fragment shader possa ser executado.

Enunciado Mínimo:
	- Uso da técnica de raycast de mapa de altura (TEXTURA 0) dentro do CUBO.
	- pode partir do algoritmo linear do Parallax mapping (Dojo feito em aula)
	- o ray-cast tem que funcionar também considerando as paredes do cubo.
	- usar número fixo de passos (ao invés de tamanho de passo fixo)
	- cor do terreno a partir do mapa de cor (TEXTURA 1)
	- cálculo da difusa, usando as normais do terreno a partir de um mapa de normais (TEXTURA 2)

Extras algoritmo:
	- busca binária após a busca linear, para melhorar a precisão do ponto de interseção com o terreno.

Extras efeito:
	- cálculo da componente especular
	- calcular as normais sem necessitar do mapa de normais
	(dica: produto vetorial entre as diferenças dos vizinhos)
	- implementar visualização diferente dependendo de um mapa de regras (TEXTURA 3):
		-- azul: água = especular alta e transparente (azul), lâmina d’água
			--- efeitos na água: textura de mar, bump mapping de mar, ondas
			--- efeito de reflexão na água (ex: pode refletir algum morro no terreno)
			--- efeito de transparência na água (para isso a lâmina d’água tem uma altura pré-definida)
				---- aplicar a lei de Snell (refração)
		-- branco: neve = especular alta (branco)
		-- preto: não há terreno = nada é renderizado nessa parte
  		--- funciona bem mesmo visto de baixo do cubo
		-- vermelho: terreno original (não muda nada)
		-- outras lógicas implementadas pelo mapa de regras
	- upload de vídeo no Youtube de 1 minuto
	
Super Extra Efeito:
	- incluir objetos implícitos (ex: esferas) junto com o terreno
	
Super Extra Algoritmo:
	- balanceamento entre as buscas linear e binária de acordo com a inclinação do raio
	- ajuste silhueta. Explicação: quando o raio sai pela lateral da parede, há uma oportunidade de com um número fixo de passos, ter mais precisão, pois o tamanho do passo pode ser menor
