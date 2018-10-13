---
title: XML スニペット |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bf1ebeb70931e2e12f056ecfbaa45a6833e031df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183964"
---
# <a name="xml-snippets"></a>XML スニペット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML エディターと呼ばれる、機能を提供する*XML スニペット*、XML ファイルをより迅速にビルドすることができます。 XML スニペットは、ファイルに挿入することで再利用できます。 XML スキーマ定義言語 (XSD) スキーマに基づいて XML データを生成することもできます。  
  
## <a name="reusable-xml-snippets"></a>再利用可能な XML スニペット  
 XML エディターには、一般的なタスクを対象としたスニペットが多数含まれています。 これによって、XML ファイルをより簡単に作成できます。 たとえば、XML スキーマを作成している場合、"Complex Type Sequence Element" スニペットと "Simple Type Element" スニペットを使用すると、作成中のファイルに次の XML テキストが挿入されます。 その後で、必要に応じて `name` の値を変更します。  
  
```  
<xs:element name="name">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="name">  
        <xs:simpleType>  
          <xs:restriction base="xs:string"></xs:restriction>  
        </xs:simpleType>  
      </xs:element>  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 スニペットは 2 つの方法で挿入できます。 **スニペットの挿入**コマンドは、カーソル位置にある XML スニペットを挿入します。 **ブロックの挿入**コマンドは、選択したテキストの周囲の XML スニペットをラップします。 両方のコマンドが使用可能ないずれかから、 **IntelliSense**サブメニュー、**編集**メニュー、またはエディターのショートカット メニューから。  
  
 詳細については、次を参照してください。[方法: XML スニペットを使用して](../xml-tools/how-to-use-xml-snippets.md)します。  
  
## <a name="schema-generated-xml-snippets"></a>スキーマを生成する XML スニペット  
 XML エディターは、XML スキーマから XML スニペットを生成する機能も備えています。 この機能を使用すると、要素に、その要素のスキーマ情報から生成された XML 要素を格納することができます。  
  
 詳細については、次を参照してください。[方法: XML スニペットからの XML スキーマを生成](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)します。  
  
## <a name="create-new-xml-snippets"></a>新しい XML スニペットを作成する  
 含まれているスニペットに加えて[!INCLUDE[msCoName](../includes/msconame-md.md)]Visual Studio の既定も作成して、独自の XML スニペットを使用することができます。  
  
 詳細については、次を参照してください。[方法: XML スニペットの作成](../xml-tools/how-to-create-xml-snippets.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)



