# Bucket-Bucket Transfer Script

O objetivo deste script é possibilitar a transferência de objetos (arquivos ou pastas) entre dois buckets Amazon S3 que possuam as mesmas credenciais IAM.

# Avisos
- O script não realiza a deleção de objetos em nenhum dos dois buckets. Caso seja informado um destino que já esteja ocupado, o comportamento é **indefinido**.

# Instruções de Uso

Para utilizar, é necessário abrir a aplicação de terminal de sua preferência (bash, zsh, powershell, cmd) e se posicionar na pasta onde está o script está armazenado.

	cd raiz/diretorio

Após isso, basta realizar a chamada do interpretador Python, informar o nome do script e passar os parâmetros necessários, conforme abaixo:

	python3 transfer.py --src_key raw/bdo/sap/t023t --dst_key uds/comercial/raw/t023t

Logo após, o script irá lhe mostrar as configurações que serão utilizadas para realizar a transferência e irá lhe pedir permissão para continuar.

	[INFO] Starting S3 Object Bucket-Bucket Transfer script.

	The script will be executed with the following parameters:

	[SRC_BUCKET]: prd-dot
	[DST_BUCKET]: dev-dot
	[SRC_KEY]: raw/bdo/sap/t023t
	[DST_KEY]: uds/comercial/raw/t023t
	
	Are you sure? (y/n)

Após a confirmação, basta aguardar até que a cópia dos objetos seja realizado.

> **Nota:** é possível desativar a confirmação ao passar o parâmetro --y, confira o item "Parâmetros".

## Parâmetros
 - **src_key:**
Parâmetro para informar qual a chave do objeto a ser copiado no bucket de origem, não pode ser iniciado ou finalizado com o caractere '/'.

	Tipo: obrigatório
	Exemplo: raw/bdo/sap/t023t

 - **dst_key:**
 Parâmetro para informar em qual chave será armazenado o objeto no bucket de destino, não pode ser iniciado ou finalizado com o caractere '/'.
 
	 Tipo: obrigatório
	Exemplo: uds/comercial/raw/t023t

 - **y:**
 Parâmetro para informar se o script deve confirmar os dados de execução.
 
	 Tipo: opcional
	Exemplo: --y

## Configurações

O script utiliza um arquivo de configurações **config.cfg** para extrair as credenciais de acesso do AWS IAM e a nomenclatura do bucket de origem e de destino.

 - **ACCESS_KEY:**
Chave de acesso do bucket

 - **SECRET_KEY:**
Chave secreta de acesso do bucket.

 - **SOURCE_BUCKET:**
Nome do bucket de origem.

 - **DEST_BUCKET:**
Nome do bucket de destino.
