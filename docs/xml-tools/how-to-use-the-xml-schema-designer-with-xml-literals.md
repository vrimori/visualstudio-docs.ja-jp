---
title: "方法: XML リテラルに XML スキーマ デザイナーを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法: XML リテラルに XML スキーマ デザイナーを使用する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、Visual Basic プロジェクトの XML リテラルに関連付けられたスキーマを表示する方法について説明します。  
  
### 新しい Visual Basic コンソール アプリケーションのプロジェクトを作成するには  
  
1.  Visual Studio 2010 を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をクリックし、次に **\[プロジェクト\]** をクリックします。**\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。**\[プロジェクトの種類\]** で **\[他の言語\]** を選択し、**\[Visual Basic\]** を選択します。**\[テンプレート\]** で \[コンソール アプリケーション\] を選択します。**\[プロジェクト名\]** フィールドに「`XMLLiterals`」と入力し、**\[場所\]** フィールドにプロジェクトの場所を入力します。**\[OK\]** をクリックします。  
  
     新しいプロジェクトが作成されます。XMLLiterals プロジェクトには、Module1.vb という 1 つの Visual Basic ソース ファイルが含まれています。  
  
### 既存の XSD ファイルをプロジェクトに追加するには  
  
1.  新しいテキスト ファイルをメモ帳で開きます。[購買発注書のスキーマ](../xml-tools/sample-xsd-file-simple-schema.md)からXML スキーマのサンプル コードをコピーし、ファイルに貼り付けます。  
  
2.  PurchaseOrderSchema.xsd という名前でファイルをどこかに保存します。  
  
3.  ソリューション エクスプローラーで、プロジェクト名を右クリックし、**\[追加\]** を選択して **\[既存の項目\]** をクリックします。**\[既存項目の追加\]** ダイアログ ボックスが表示されます。PurchaseOrderSchema.xsd ファイルを参照して選択し、**\[追加\]** をクリックします。  
  
     XMLLiterals プロジェクトに、Module1.vb および PurchaseOrderSchema.xsd という 2 つのファイルが含まれるようになります。  
  
### プロジェクトに含まれる XSD ファイルに基づいて XML リテラルの Visual Basic コードを追加するには  
  
1.  Module1.vb ファイルのコードを次のコードに置き換えます。  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  XML リテラルまたは XML 名前空間インポートの XML ノードを右クリックして、**\[スキーマ エクスプローラーで表示\]** をクリックします。  
  
     XML スキーマ エクスプローラーが、XML スキーマ セットに関連付けられた XML リテラルを持つ Visual Basic ファイルと並んで表示されます。