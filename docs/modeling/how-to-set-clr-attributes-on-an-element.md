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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932273"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>方法: 要素の CLR 属性を設定する
カスタム属性は、ドメイン要素、図形、コネクタ、およびダイアグラムを追加できる特別な属性です。 継承する任意の属性を追加することができます、`System.Attribute`クラス。

### <a name="to-add-a-custom-attribute"></a>カスタム属性を追加するには

1.  **DSL エクスプ ローラー**、カスタム属性を追加する要素を選択します。

2.  **プロパティ**ウィンドウ、次へ を**カスタム属性**プロパティで、参照 をクリックします (**...**) アイコン。

     **属性の編集** ダイアログ ボックスが表示されます。

3.  **名前**列、 をクリックして**\<属性の追加 >** 属性の名前を入力します。 ENTER キーを押します。

4.  属性名の下にある行は、かっこを示しています。 この行に入力属性のパラメーターの型 (たとえば、 `string`)、し、ENTER キーを押します。

5.  **Name プロパティ**列で、たとえば、適切な名前を入力`MyString`します。

6.  **[OK]** をクリックします。

     **カスタム属性**プロパティは、次の形式で属性を表示するようになりました。

     `[` *AttributeName* `(` *ParameterName* `=` *Type* `)]`

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)