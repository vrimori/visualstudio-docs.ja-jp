---
title: '方法: XML リテラルと XML スキーマ デザイナーを使用して |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cb0ba92afd8a3c8ab915d72237a5251643b32669
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536971"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>方法: XML リテラルに XML スキーマ デザイナーを使用する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: XML リテラルと XML スキーマ デザイナーを使用して](https://docs.microsoft.com/visualstudio/xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals)します。  
  
  
このトピックでは、Visual Basic プロジェクトの XML リテラルに関連付けられたスキーマを表示する方法について説明します。  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>新しい Visual Basic コンソール アプリケーションのプロジェクトを作成するには  
  
1.  Visual Studio 2010 を起動します。  
  
2.  **ファイル**メニューの **新規**、し、**プロジェクト**します。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。 **プロジェクトの種類**を選択します**他の言語、** 選び**Visual Basic**します。 **テンプレート**、コンソール アプリケーションを選択します。 入力`XMLLiterals`で、**名前**フィールドとプロジェクトの場所、**場所**フィールド。 **[OK]** をクリックします。  
  
     新しいプロジェクトが作成されます。 XMLLiterals プロジェクトには、Module1.vb という 1 つの Visual Basic ソース ファイルが含まれています。  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>既存の XSD ファイルをプロジェクトに追加するには  
  
1.  開いている新しいテキスト ファイルを Notepad.Copy から XML スキーマのサンプル コード[購買発注書スキーマ](../xml-tools/sample-xsd-file-simple-schema.md)ファイルに貼り付けます。  
  
2.  PurchaseOrderSchema.xsd という名前でファイルをどこかに保存します。  
  
3.  ソリューション エクスプ ローラーでプロジェクトの名前を右クリックして**追加**、し、**既存の項目.**. **既存項目の追加** ダイアログ ボックスが表示されます。 PurchaseOrderSchema.xsd ファイルを参照し、選択しをクリックして**追加**します。  
  
     XMLLiterals プロジェクトに、Module1.vb および PurchaseOrderSchema.xsd という 2 つのファイルが含まれるようになります。  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>プロジェクトに含まれる XSD ファイルに基づいて XML リテラルの Visual Basic コードを追加するには  
  
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
  
2.  XML リテラルまたは XML 名前空間インポートでの任意の XML ノードを右クリックして**スキーマ エクスプ ローラーで表示する**します。  
  
     XML スキーマ エクスプローラーが、XML スキーマ セットに関連付けられた XML リテラルを持つ Visual Basic ファイルと並んで表示されます。



