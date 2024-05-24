<H2>CRIAÇÃO DE LOV</H2>

<span>Para criação de um lov com tabela nova</span>

<p>1º Monta a tabela no banco de dados conforme exemplo onde faremos a conversão do campo enum tipopub para uma tabela em banco de dados.</p>
<strong>
  **** criação da tabela ****	</br>
  
  CREATE TABLE TIPOPUBLICACAO (	</br>
    TIPOPUB    NUMBER(10) NOT NULL ENABLE,	</br>
	  DESCRICAO  VARCHAR2(100)	</br>
  )		</br>
  /		</br>
  ALTER TABLE TIPOPUBLICACAO ADD CONSTRAINT TIPOPUBLICACAO_PK PRIMARY KEY (TIPOPUB)	</br>
 /	</br>

  **** descricao das colunas ****	</br>
  
  COMMENT ON COLUMN TIPOPUBLICACAO.TIPOPUB IS 'ID tipo publicacao'	</br>
  /	</br>
  COMMENT ON COLUMN TIPOPUBLICACAO.DESCRICAO IS 'Descricao tipo publicacao'	</br>
  /	</br>

  **** insersão de dados na tabela ****	</br>
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(1, 'DJE')	</br>
  /	</br>
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(2, 'DOU')	</br>
  /	</br>
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(3, 'DOE')	</br>
  /	</br>
  INSERT INTO TIPOPUBLICACAO(TIPOPUB, DESCRICAO)VALUES(4, 'DJEA')	</br>
  /	</br>

  **** adição do campo (tipopub == tipobublicacao) na tabela documentos onde ele sera inserido. ****	</br>
  ALTER TABLE DOCUMENTOS ADD TIPOPUB NUMBER(10)	</br>	</br>
  /	</br>

  **** criação da chave estrangeira e vinculo da tabela documentos/tipopublicaçcao ****
  ALTER TABLE DOCUMENTOS ADD CONSTRAINT DOCUMENTOS_TIPOPUB_FK FOREIGN KEY (TIPOPUB)  REFERENCES TIPOPUBLICACAO(TIPOPUB)	</br>
  /	</br>
  COMMIT	</br>
  /	</br>
  </strong>

  
