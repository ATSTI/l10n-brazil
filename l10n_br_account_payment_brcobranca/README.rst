==================================
L10n Br Account Payment BRCobranca
==================================

.. 
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! This file is generated by oca-gen-addon-readme !!
   !! changes will be overwritten.                   !!
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
   !! source digest: sha256:6818067d9dd4bd1add449d3aa4ed91703418d1e21f7244751501f91f0a730e09
   !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

.. |badge1| image:: https://img.shields.io/badge/maturity-Beta-yellow.png
    :target: https://odoo-community.org/page/development-status
    :alt: Beta
.. |badge2| image:: https://img.shields.io/badge/licence-AGPL--3-blue.png
    :target: http://www.gnu.org/licenses/agpl-3.0-standalone.html
    :alt: License: AGPL-3
.. |badge3| image:: https://img.shields.io/badge/github-OCA%2Fl10n--brazil-lightgray.png?logo=github
    :target: https://github.com/OCA/l10n-brazil/tree/14.0/l10n_br_account_payment_brcobranca
    :alt: OCA/l10n-brazil
.. |badge4| image:: https://img.shields.io/badge/weblate-Translate%20me-F47D42.png
    :target: https://translation.odoo-community.org/projects/l10n-brazil-14-0/l10n-brazil-14-0-l10n_br_account_payment_brcobranca
    :alt: Translate me on Weblate
.. |badge5| image:: https://img.shields.io/badge/runboat-Try%20me-875A7B.png
    :target: https://runboat.odoo-community.org/builds?repo=OCA/l10n-brazil&target_branch=14.0
    :alt: Try me on Runboat

|badge1| |badge2| |badge3| |badge4| |badge5|

**Português**
Esse modulo implementa o CNAB usando a biblioteca BRCobranca
https://github.com/kivanio/brcobranca .

**English**
This module implement brazilian bank splips('Boletos Bancarios') by using
BRCobranca(https://github.com/kivanio/brcobranca).

**Table of contents**

.. contents::
   :local:

Installation
============

**Português**
O modulo depende do:

* l10n_br_account_payment_order
* account_move_base_import

**English**
This module depends on:

* l10n_br_account_payment_order
* account_move_base_import

Configuration
=============

**Português**
Para configurar esse modulo é preciso:

* Rodar a biblioteca BRCobranca como um micro-serviço https://github.com/akretion/boleto_cnab_api .
* Informar a variável de ambiente **BRCOBRANCA_API_URL** no arquivo de configuração do Odoo ou se estiver usando o docky na seção enviroment https://github.com/akretion/docky-odoo-brasil/blob/12.0/docker-compose.yml#L3 , exemplo:
  **BRCOBRANCA_API_URL=http://boleto_cnab_api:9292**
* Verifique se os Códigos de Movimento do CNAB a ser usado existem em Faturamento > Configurações > Administração > Códigos de Instrução do Movimento CNAB, se for necessário criar considere fazer um PR para adicionar como dados aqui https://github.com/OCA/l10n-brazil/blob/12.0/l10n_br_account_payment_order/data/l10n_br_cnab_mov_instruction_code_data.xml .
* Verifique se os Códigos de Retorno do Movimento do CNAB a ser usado existem em Faturamento > Configurações > Administração > Códigos de Retorno de Movimento CNAB, se for necessário criar considere fazer um PR para adicionar como dados aqui https://github.com/OCA/l10n-brazil/blob/12.0/l10n_br_account_payment_order/data/l10n_br_cnab_return_move_code_data.xml .
* Criar a Conta Bancária referente ao CNAB em Faturamento > Configurações > Contabilidade > Contas Bancárias .
* Automaticamente será criado um Diário Contábil referente a conta bancária em Faturamento > Configurações > Contabilidade > Diários na aba **Informações Referentes a Importação** informe as configurações de Retorno do CNAB nos campos "Tipo de Importação", "Conta de Recebimento/Pagamento", "Criação de Contra-Partida" e se deve ser feita a reconciliação automática ao importar o arquivo em "Reconciliar Automaticamente o Retorno de Pagamento".
* Em Faturamento > Configurações > Administração > Modos de Pagamento criar um Modo de Pagamento com as informações do CNAB, no campo "Diário de Banco Fixo" informar o Diário Contábil da conta bancária e se for o caso, e é recomendado, marcar a opção "Adicionar automaticamente ao validar a fatura" para não ser preciso fazer manualmente.
* Caso o CNAB e Banco escolhidos possua um campo especifico que seja preciso implementar considere fazer um PR no modulo l10n_br_account_payment_order aqui https://github.com/OCA/l10n-brazil/blob/12.0/l10n_br_account_payment_order/models/l10n_br_cnab_boleto_fields.py#L307 .
* Configure as permissões de acesso dos usuários, as opções são CNAB "Usuário" e "Gerente".

**English**
To configure this module, you need to:

* Run BRCobranca as micro-service https://github.com/akretion/boleto_cnab_api.
* Inform the envoriment variable BRCOBRANCA_API_URL in the config odoo file or if are use docky in the section enviroment https://github.com/akretion/docky-odoo-brasil/blob/12.0/docker-compose.yml#L3 , example:
  **BRCOBRANCA_API_URL=http://boleto_cnab_api:9292**
* Check if the CNAB Instruction Movement Code to be use exist in Invoicing > Configuration > Management > CNAB Movement Instruction Code if necessary create please consider make PR to add as data in https://github.com/OCA/l10n-brazil/blob/12.0/l10n_br_account_payment_order/data/l10n_br_cnab_mov_instruction_code_data.xml .
* Check if the CNAB Return Move Code to be use exist in Invoicing > Configuration > Management > CNAB Return Move Code if necessary create please consider make PR to add as data in https://github.com/OCA/l10n-brazil/blob/12.0/l10n_br_account_payment_order/data/l10n_br_cnab_return_move_code_data.xml .
* Create an Bank Account referent of CNAB in Invoicing > Configuration > Accounting > Bank Accounts .
* Automatic will be create an Account Journal refer to bank account in Invoicing > Configuration > Accounting > Journals in tab **Import related infos** inform parameters of CNAB Return in fields "Type of Import", "Receivable/Payable Account", "Create Counterpart", and if should make automatic reconciliation when import the file in "Automatic Reconcile payment returns".
* In Invoicing > Configuration > Management > Payment Modes create an Payment Mode with CNAB information, in the field "Fixed Bank Journal" inform the Account Journal of bank account and mark if "Automatically add when validating the invoice" so that you don't have to do it manually.
* Configure user access permissions, CNAB options are "User" and "Manager".

Usage
=====

**Português**

* Ao criar e Confirmar uma Fatura que tem um Modo de Pagamento que seja CNAB deverá aparecer o botão de "Imprimir Boleto".
* Caso esteja marcado no Modo de Pagamento a opção de "Adicionar automaticamente ao validar a fatura" será criada ou adicionada em uma Ordem de Pagamento as linhas de pagamentos do CNAB, se a opção não estiver marcada será preciso fazer isso manualmente podendo ser feito tanto na Fatura quanto na Ordem de Pagamento.
* Ao Confirmar essa Ordem de Pagamento será possível gerar o arquivo de Remessa CNAB a ser enviado ao Banco, é importante confirmar o envio do arquivo alterando o status da ordem para "Arquivo Enviado", essa informação é usada para validar se existe uma instrução CNAB pendente antes de se poder criar outra.
* Alterações de CNAB como Alteração da Data de Vencimento, Protesto, Conceder Abatimento e etc podem ser feitas na própria Fatura em Faturamento > Clientes > Faturas na aba Recebimentos na última coluna existe o botão "Atualizar Informação CNAB" ao clicar em uma linha essa opção também aparece, ao fazer uma alteração é criada ou adicionada em uma Ordem de Pagamento a Instrução de Movimento CNAB selecionada.
* A importação do arquivo CNAB de Retorno pode ser feita em Pagamentos > Importar arquivo Batch ou no próprio Diário em Faturamento > Configurações > Contabilidade > Diários na aba **Informações Referentes a Importação** o botão Importar arquivo Batch.
* Toda importação de arquivo de retorno cria uma LOG que pode ser consultado em Pagamentos > LOG de Retorno CNAB.
* Caso o Código de Retorno CNAB recebido seja um dos "Códigos de Liquidação do Retorno do Movimento" do Modo de Pagamento será criado uma Entrada de Diário com os valores quando existirem de desconto, juros/mora, tarifa bancaria, abatimento e valor a ser reconciliado com a linha da Fatura referente, os lançamentos são separados de acordo com as Contas Contabéis definidas no Modo de Pagamento, a linha para reconciliar a linha da Fatura precisam ser iguais por isso o valor é:
  valor_recebido_calculado = (valor_recebido + valor_desconto + valor_abatimento) - valor_juros_mora
* Quando marcada a opção de "Reconciliação Automatica" /a Entrada de Diário será movida para o status Lançado automaticamente ao importar o arquivo, se não estiver marcada isso deverá ser feito manualmente.

**English**

* When creating and confirming an Invoice that has a Payment Mode that is CNAB, the button should appear "Print Boleto".
* If the option to "Add automatically when validating the invoice" is marked in the Payment Mode CNAB payment lines will be created or added to a Payment Order, if the option is not marked, you will need to do this manually, which can be done both in the Invoice and in the Payment Order.
* By confirming this Payment Order it will be possible to generate the CNAB Remessa file to be sent to the Bank, it is important to confirm the upload of the file by changing the order status to "File Uploaded", this information is used to validate if there is a pending CNAB instruction before another one can be created.
* CNAB changes such as Change Due Date, Protest, Grant Rebate, etc. can be made in the Invoice itself in Invoicing > Customers > Invoices in the Receivable tab in the last column there is the button "Update CNAB Information" when clicking on a line this option also appears, when making a change it is created or added to a Payment Order the selected CNAB Movement Instruction.
* The import of the Return CNAB file can be done in Payments > Import Batch file or in the same Journal in Invoicing > Configuration > Accounting > Journals in the tab **Import related infos** the Import Batch File button.
* Every return file import creates a LOG that can be consulted in Payments > CNAB Return LOG.
* If the CNAB Return Code received is one of the "CNAB Liquidity Return Move Code" of the Payment Mode, a Journal Entry will be created with the values when there are discount, interest, tariff charge, rebate and amount to be reconciled with the referring Invoice line, entries are separated according to the Accounts defined in the Payment Mode, the line to reconcile the Invoice line need be equal so the value is:
  calculated_value_receive = (receive_amount + discount_amount + rebate_amount) - interest_amount
* When the "Automatic Reconciliation" option is checked, the Entry of Journal will be moved to the status Posted automatically when importing the file, if not checked it should be done manually.

Known issues / Roadmap
======================

* Incluir a posssibilidade de imprimir o boleto no menu Imprimir da Fatura, na v12 aparentemente não é possível chamar um metodo apenas um QWeb, verificar na migração para outras versões.

Changelog
=========

14.0.1.0.0 (2022-05-26)
~~~~~~~~~~~~~~~~~~~~~~~

* [MIG] Migration

12.0.1.0.0 (2021-05-07)
~~~~~~~~~~~~~~~~~~~~~~~

* [MIG] Finish migration
* [IMP] Integrate with module account_move_base_import used to import CNAB file
* [IMP] Make possible automatic reconciliation and register the values of Fees, Tariff Bank, Rebate in configured accounts.

12.0.1.0.0 (2020-06-12)
~~~~~~~~~~~~~~~~~~~~~~~

* [MIG] Start Migration

10.0.1.0.0 (2019-05-30)
~~~~~~~~~~~~~~~~~~~~~~~

* [MIG] Migration

8.0.1.0.0 (2018-01-29)
~~~~~~~~~~~~~~~~~~~~~~~

* [REF] Maked functional to print Boleto, create CNAB file and import CNAB as Extrat Bank the user should be resolved manully the divergences between the values( Fee, Tariff Bank, Rebate, etc).

8.0.1.0.0 (2017-07-01)
~~~~~~~~~~~~~~~~~~~~~~~

* [NEW] First version

Bug Tracker
===========

Bugs are tracked on `GitHub Issues <https://github.com/OCA/l10n-brazil/issues>`_.
In case of trouble, please check there if your issue has already been reported.
If you spotted it first, help us to smash it by providing a detailed and welcomed
`feedback <https://github.com/OCA/l10n-brazil/issues/new?body=module:%20l10n_br_account_payment_brcobranca%0Aversion:%2014.0%0A%0A**Steps%20to%20reproduce**%0A-%20...%0A%0A**Current%20behavior**%0A%0A**Expected%20behavior**>`_.

Do not contact contributors directly about support or help with technical issues.

Credits
=======

Authors
~~~~~~~

* Akretion

Contributors
~~~~~~~~~~~~

* `Akretion <https://akretion.com/pt-BR>`_:
  * Raphaël Valyi <raphael.valyi@akretion.com.br>
  * Magno Costa <magno.costa@akretion.com.br>

* `Engenere <https://engenere.one>`_:
  * Antônio S. Pereira Neto <neto@engenere.one>

Other credits
~~~~~~~~~~~~~

The development of this module has been financially supported by:

* AKRETION LTDA - https://akretion.com/pt-BR

Maintainers
~~~~~~~~~~~

This module is maintained by the OCA.

.. image:: https://odoo-community.org/logo.png
   :alt: Odoo Community Association
   :target: https://odoo-community.org

OCA, or the Odoo Community Association, is a nonprofit organization whose
mission is to support the collaborative development of Odoo features and
promote its widespread use.

.. |maintainer-rvalyi| image:: https://github.com/rvalyi.png?size=40px
    :target: https://github.com/rvalyi
    :alt: rvalyi
.. |maintainer-mbcosta| image:: https://github.com/mbcosta.png?size=40px
    :target: https://github.com/mbcosta
    :alt: mbcosta

Current `maintainers <https://odoo-community.org/page/maintainer-role>`__:

|maintainer-rvalyi| |maintainer-mbcosta| 

This module is part of the `OCA/l10n-brazil <https://github.com/OCA/l10n-brazil/tree/14.0/l10n_br_account_payment_brcobranca>`_ project on GitHub.

You are welcome to contribute. To learn how please visit https://odoo-community.org/page/Contribute.
