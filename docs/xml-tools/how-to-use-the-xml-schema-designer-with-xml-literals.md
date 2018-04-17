---
title: '方法: XML リテラルと XML スキーマ デザイナーを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 504b063ccbc9646755891fc0eea3647a5594b213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>方法: XML リテラルに XML スキーマ デザイナーを使用する
このトピックでは、Visual Basic プロジェクトの XML リテラルに関連付けられたスキーマを表示する方法について説明します。  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>新しい Visual Basic コンソール アプリケーションのプロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **ファイル**メニューの **新規**、し、**プロジェクト**です。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。 **プロジェクトの種類****他の言語**し、 **Visual Basic**です。 **テンプレート**、コンソール アプリケーションを選択します。 入力`XMLLiterals`で、**名前**フィールドとプロジェクトの場所で、**場所**フィールドです。 **[OK]**をクリックします。  
  
     新しいプロジェクトが作成されます。 XMLLiterals プロジェクトには、Module1.vb という 1 つの Visual Basic ソース ファイルが含まれています。  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>既存の XSD ファイルをプロジェクトに追加するには  
  
1.  開いている新しいテキスト ファイルを Notepad.Copy から XML スキーマのサンプル コード[購買発注書スキーマ](../xml-tools/sample-xsd-file-simple-schema.md)し、ファイルに貼り付けます。  
  
2.  PurchaseOrderSchema.xsd という名前でファイルをどこかに保存します。  
  
3.  ソリューション エクスプ ローラーでプロジェクトの名前を右クリックし、選択**追加**、し、[**既存アイテム.**.**AddExisting 項目**] ダイアログ ボックスが表示されます。 PurchaseOrderSchema.xsd ファイルを選択し、をクリックして**追加**です。  
  
     XMLLiterals プロジェクトに、Module1.vb および PurchaseOrderSchema.xsd という 2 つのファイルが含まれるようになります。  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>プロジェクトに含まれる XSD ファイルに基づいて XML リテラルの Visual Basic コードを追加するには  
  
1.  Module1.vb ファイルのコードを次のコードに置き換えます。  
  
   ```vb
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
  
2.  XML リテラルまたは XML 名前空間インポートでの任意の XML ノードを右クリックし **スキーマ エクスプ ローラーで表示**です。  
  
     XML スキーマ エクスプローラーが、XML スキーマ セットに関連付けられた XML リテラルを持つ Visual Basic ファイルと並んで表示されます。