---
title: "方法: 要素に CLR 属性を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7dcbd0005b80887dae91249a6781a6982414b9e5
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-set-clr-attributes-on-an-element"></a>方法: 要素の CLR 属性を設定する
カスタム属性は、ドメイン要素、図形、コネクタ、およびダイアグラムに追加できる特別な属性です。 継承する任意の属性を追加する、`System.Attribute`クラスです。  
  
### <a name="to-add-a-custom-attribute"></a>カスタム属性を追加するには  
  
1.  **DSL エクスプ ローラー**、カスタム属性を追加する要素を選択します。  
  
2.  **プロパティ** の横のウィンドウで、**カスタム属性**プロパティには、参照 をクリックして (**.**) icon.  
  
     **属性を編集** ダイアログ ボックスが表示されます。  
  
3.  **名** 列で、をクリックして**\<属性を追加 >**し、目的の属性の名前を入力します。 ENTER キーを押します。  
  
4.  属性名の下にある行は、かっこを示しています。 次の行に入力属性のパラメーターの型 (たとえば、 `string`)、ENTER キーを押します。  
  
5.  **Name プロパティ** 列で、たとえば、適切な名前を入力`MyString`します。  
  
6.  **[OK]** をクリックします。  
  
     **カスタム属性**プロパティは、次の形式で属性を表示するようになりました。  
  
     `[`*AttributeName* `(` *ParameterName* `=` *Type*`)]`  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
