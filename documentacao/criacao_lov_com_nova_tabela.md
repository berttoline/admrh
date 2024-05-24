<H2>CRIAÇÃO DE LOV</H2>

<span>Para criação de um lov com tabela nova</span>

<p>1º Monta a tabela no banco de dados conforme exemplo onde faremos a conversão do campo enum tipopub para uma tabela em banco de dados.</p>
<strong>
  **** criação da tabela ****
  
  CREATE TABLE TIPOPUBLICACAO (
    TIPOPUB    NUMBER(10) NOT NULL ENABLE, 
	  DESCRICAO  VARCHAR2(100)
  )
  /
  ALTER TABLE TIPOPUBLICACAO ADD CONSTRAINT TIPOPUBLICACAO_PK PRIMARY KEY (TIPOPUB)
  /

  **** descricao das colunas ****
  
  COMMENT ON COLUMN TIPOPUBLICACAO.TIPOPUB IS 'ID tipo publicacao'
  /
  COMMENT ON COLUMN TIPOPUBLICACAO.DESCRICAO IS 'Descricao tipo publicacao'
  /

  **** insersão de dados na tabela ****
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(1, 'DJE')
  /
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(2, 'DOU')
  /
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(3, 'DOE')
  /
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(4, 'DJEA')
  /

  **** adição do campo (tipopub == tipobublicacao) na tabela documentos onde ele sera inserido. ****
  ALTER TABLE DOCUMENTOS ADD TIPOPUB NUMBER(10)
  /

  **** criação da chave estrangeira e vinculo da tabela documentos/tipopublicaçcao ****
  ALTER TABLE DOCUMENTOS ADD CONSTRAINT DOCUMENTOS_TIPOPUB_FK FOREIGN KEY (TIPOPUB)  REFERENCES TIPOPUBLICACAO(TIPOPUB)
  /
  COMMIT
  /
  </strong>

  
