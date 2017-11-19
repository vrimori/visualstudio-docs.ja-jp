---
title: "方法: 要素の CLR 属性を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.EditAttributesDialog
helpviewer_keywords: Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: "19"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 7dcbd0005b80887dae91249a6781a6982414b9e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>方法: 要素の CLR 属性を設定する
カスタム属性は、ドメインの要素、図形、コネクタ、およびダイアグラムを追加できる特別な属性です。 継承する任意の属性を追加することができます、`System.Attribute`クラスです。  
  
### <a name="to-add-a-custom-attribute"></a>カスタム属性を追加するには  
  
1.  **DSL のエクスプ ローラー**、カスタム属性を追加する要素を選択します。  
  
2.  **プロパティ**ウィンドウで、[次へ] を**カスタム属性**プロパティ、[参照] をクリックして (**.**) のアイコン。  
  
     **属性を編集** ダイアログ ボックスが表示されます。  
  
3.  **名前**列で、をクリックして**\<属性を追加 >**し、属性の名前を入力します。 ENTER キーを押します。  
  
4.  属性名の下にある行は、かっこを示しています。 この行に入力属性のパラメーターの型 (たとえば、 `string`)、ENTER キーを押します。  
  
5.  **Name プロパティ**列で、たとえば、適切な名前を入力`MyString`です。  
  
6.  **[OK]** をクリックします。  
  
     **カスタム属性**プロパティは、次の形式で属性を表示するようになりました。  
  
     `[`*AttributeName* `(` *ParameterName* `=` *型*`)]`  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)