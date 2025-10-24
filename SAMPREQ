      *****************************************************************
      *                                                               *
      *         SAMPLE COBOL PARA PREENCHIMENTO SIMPLIFICADO          *
      *              IBM EXPERT LABS (Gabriel Paiva)                  *
      *                                                               *
      *****************************************************************
      *                                                               *
      *     Alterações necessárias:                                   *
      *	                                                              *
      *     1 - Troque as 2 variáveis <nome-do-programa> pelo nome    * 
      *	    desejado para identificar o programa.                     *
      *                                                               *
      *	    2 - Troque <arquivo-request>, <arquivo-response> e        *
      *	    <arquivo-info>, pelos seus respectivos arquivos.          * 
      *                                                               *
      *	    3 - Preencha os campos da request.                        *
      *	                                                              *
      *     4 - Defina o que será feito em caso de uma resposta bem   *  
      *	    sucedida.                                                 *	             	        
      *                                                               *
      *****************************************************************
       IDENTIFICATION DIVISION.
       PROGRAM-ID. <nome-do-programa>.
       DATA DIVISION.
       WORKING-STORAGE SECTION.

       COPY 'BAQRINFO'.

       01  REQUEST.
           COPY <arquivo-request>.
       01  RESPONSE.
           COPY <arquivo-response>.
       01  API-INFO-API1.
           COPY <arquivo-info>.

      * Request and Response data structures
       01 BAQ-REQUEST-PTR             USAGE POINTER.
       01 BAQ-REQUEST-LEN             PIC S9(9) COMP-5 SYNC.
       01 BAQ-RESPONSE-PTR            USAGE POINTER.
       01 BAQ-RESPONSE-LEN            PIC S9(9) COMP-5 SYNC.
       77 COMM-STUB-PGM-NAME             PIC X(8) VALUE 'BAQCSTUB'.

       LINKAGE SECTION.

      
       PROCEDURE DIVISION.
       MAINLINE SECTION.

           INITIALIZE REQUEST.
           INITIALIZE RESPONSE.

           SET BAQ-REQUEST-PTR TO ADDRESS OF REQUEST.
           MOVE LENGTH OF REQUEST TO BAQ-REQUEST-LEN.
           SET BAQ-RESPONSE-PTR TO ADDRESS OF RESPONSE.
           MOVE LENGTH OF RESPONSE TO BAQ-RESPONSE-LEN.


      ********************************************************
      *	
      * Nesta secão, o desenvolvedor deve preencher os campos da
      * estrutura REQUEST (definida no copybook <arquivo-request>).
      * Cada campo corresponde a um parâmetro da API que 
      * será chamada pelo z/OS Connect.
      *
      * Instruções gerais:
      * - Utilize os nomes dos campos definidos no copybook da API.
      * - Preencha cada campo com os valores de entrada necessários.
      * - Se houver campos opcionais, podem ser movidos com espaços.
      * - Exemplo genérico:
      *     MOVE '<valor>' TO <campo-do-request>.
      *
      * O objetivo é garantir que todos os campos obrigatórios
      * estejam corretamente preenchidos antes da chamada 
      *  ao BAQCSTUB.
      *
      ********************************************************

           CALL COMM-STUB-PGM-NAME USING
                           BY REFERENCE   API-INFO-API1
                           BY REFERENCE   BAQ-REQUEST-INFO
                           BY REFERENCE   BAQ-REQUEST-PTR
                           BY REFERENCE   BAQ-REQUEST-LEN
                           BY REFERENCE   BAQ-RESPONSE-INFO
                           BY REFERENCE   BAQ-RESPONSE-PTR
                           BY REFERENCE   BAQ-RESPONSE-LEN.

      * The BAQ-RETURN-CODE field in 'BAQRINFO' indicates whether this
      * API call is successful.

      * When BAQ-RETURN-CODE is 'BAQ-SUCCESS', response is
      * successfully returned and fields in RESPONSE copybook
      * can be obtained.
           IF BAQ-SUCCESS THEN
      ************************************************************
      *       Inclua aqui o processamento dos dados retornados
      *       em caso de sucesso.
      *       Utilize os campos definidos no copybook RESPONSE
      *       para acessar o conteúdo da resposta da API.
      ************************************************************
           
           ELSE
              EVALUATE TRUE
                 WHEN BAQ-ERROR-IN-API
                   DISPLAY "API RETURN ERROR: " BAQ-STATUS-CODE
                   DISPLAY "API RETURN ERROR MESSAGE: "
                                             BAQ-STATUS-MESSAGE
                 WHEN BAQ-ERROR-IN-ZCEE
                   DISPLAY "SERVER RETURN ERROR: " BAQ-STATUS-CODE
                   DISPLAY "SERVER RETURN ERROR MESSAGE: "
                                            BAQ-STATUS-MESSAGE
                 WHEN BAQ-ERROR-IN-STUB
                   DISPLAY "STUB RETURN ERROR: " BAQ-STATUS-CODE
                   DISPLAY "STUB RETURN ERROR MESSAGE: "
                                            BAQ-STATUS-MESSAGE
              END-EVALUATE
           END-IF.

           STOP RUN.
       END PROGRAM <nome-do-programa>.
