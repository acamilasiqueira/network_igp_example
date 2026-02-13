# Network - Exemplo de configuração IGP
IGP é um conjunto de protocolos utilizados dentro de uma mesmo Sistema Autônomo (AS) para trocar informações de rotas entre roteadores de uma mesma organização.
É o mecanismo que permite que roteadores internos de uma empresa, datacenter ou backbone corporativo aprendam a atualizem rotas automaticamente.

##

### Protocolos 
<p>👉 <strong>RIP (Routing Information Protocol)</strong></p>

<p>
<strong>Tipo:</strong> Distance Vector<br>
<strong>Métrica:</strong> Hop Count (número de saltos)<br>
<strong>Limite:</strong> 15 saltos<br>
<strong>Convergência:</strong> lenta
</p>

<p>
Rip é historicamente importante, mas praticamente obsoleto em ambientes médios e grandes.
</p>

<p>
✅ <strong>Pontos positivos:</strong> simples de configurar e baixo overhead<br>
❌ <strong>Pontos negativos:</strong> escalabilidade limitada, convergência lenta e não suporte VLSM no RIP v1<br>
🧭 <strong>Uso recomendado:</strong> apenas laboratórios ou redes muito pequenas
</p>

<hr>

<p>👉 <strong>OSPF (Open Shortest Path First)</strong></p>

<p>
<strong>Tipo:</strong> Link-State<br>
<strong>Métrica:</strong> Custo baseada na banda (cost = 100Mbps / bandwidth)<br>
<strong>Limite:</strong> Sem limite prático de hops<br>
<strong>Convergência:</strong> rápida (baseada em SPF)
</p>

<p>
OSPF mantém um banco de dados chamado LSDB (Link State Database) e todos os roteadores da mesma área possuem uma cópia idêntica.
</p>

<p>
✅ <strong>Pontos positivos:</strong> escalável, convergência rápida, suporte a VLSM e padronizado<br>
❌ <strong>Pontos negativos:</strong> mais complexo que RIP, consome mais recurso e se configurado incorretamente pode causar instabilidade<br>
🧭 <strong>Uso recomendado:</strong> redes corporativas médias e grandes
</p>

<hr>

<p>👉 <strong>EIGRP (Enhanced Interior Gateway Routing Protocol)</strong></p>

<p>
<strong>Tipo:</strong> Híbrido (Advanced Distance Vector)<br>
<strong>Métrica:</strong> Banda + Delay (por padrão)<br>
<strong>Limite:</strong> Sem limite fixo de hops (máximo teórico 255)<br>
<strong>Convergência:</strong> muito rápida (algoritmo DUAL)
</p>

<p>
EIGRP usa o algoritmo DUAL (Diffusing Update Algorithm) que evita loops antes mesmo de instalar rotas.
</p>

<p>
✅ <strong>Pontos positivos:</strong> convergência extremamente rápida, configuração simples e uso eficiente de banda<br>
❌ <strong>Pontos negativos:</strong> historicamente proprietário CISCO e escalabilidade menor que IS-IS em ambientes gigantes<br>
🧭 <strong>Uso recomendado:</strong> ambientes CISCO corporativos
</p>

<hr>

<p>👉 <strong>IS-IS (Intermediate System to Intermediate System)</strong></p>

<p>
<strong>Tipo:</strong> Link-State<br>
<strong>Métrica:</strong> Custo configurável (default 10 por interface)<br>
<strong>Limite:</strong> Altamente escalável<br>
<strong>Convergência:</strong> Muito rápida
</p>

<p>
IS-IS opera diretamente sobre camada 2 (CLNS), não depende de IP para formar adjacências.
</p>

<p>
✅ <strong>Pontos positivos:</strong> extremamente escalável, excelente para backbone e melhor para grandes topologias<br>
❌ <strong>Pontos negativos:</strong> mais complexo e menos comum em pequenas empresas<br>
🧭 <strong>Uso recomendado:</strong> ISPs e grandes datacenter
</p>
