---
title: '方法: 要素の CLR 属性を設定する'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ceca2556e269d554d40e025e5edcb91753149622
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>方法: 要素の CLR 属性を設定する
カスタム属性は、ドメインの要素、図形、コネクタ、およびダイアグラムを追加できる特別な属性です。 継承する任意の属性を追加することができます、`System.Attribute`クラスです。

### <a name="to-add-a-custom-attribute"></a>カスタム属性を追加するには

1.  **DSL のエクスプ ローラー**、カスタム属性を追加する要素を選択します。

2.  **プロパティ**ウィンドウで、[次へ] を**カスタム属性**プロパティ、[参照] をクリックして (**.**) のアイコン。

     **属性を編集** ダイアログ ボックスが表示されます。

3.  **名前**列で、をクリックして**\<属性を追加 >** し、属性の名前を入力します。 ENTER キーを押します。

4.  属性名の下にある行は、かっこを示しています。 この行に入力属性のパラメーターの型 (たとえば、 `string`)、ENTER キーを押します。

5.  **Name プロパティ**列で、たとえば、適切な名前を入力`MyString`です。

6.  **[OK]** をクリックします。

     **カスタム属性**プロパティは、次の形式で属性を表示するようになりました。

     `[` *AttributeName* `(` *ParameterName* `=` *型* `)]`

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)