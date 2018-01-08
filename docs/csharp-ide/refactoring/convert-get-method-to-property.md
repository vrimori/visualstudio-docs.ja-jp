---
title: "Get メソッドをリファクタリング (c#) プロパティに変換します |。Microsoft ドキュメント"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 71ff3db81be256bdb82413d04b2f939b706c6586
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>プロパティに Get メソッドに変換/プロパティを Get メソッドに変換します。
## <a name="convert-get-method-to-property"></a>プロパティに Get メソッドに変換します。
**新機能:**プロパティ (および必要に応じて、Set メソッド)、Get メソッドに変換することができ、その逆です。

****を任意のロジックを含まない Get メソッドがあります。

**どう：**

1. Get メソッド名にカーソルを置きます。

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**プロパティとメソッドを置き換える**プレビュー ウィンドウのポップアップからです。 Set メソッドがあれば、変換することも、Set メソッドこの時点でを選択して**置換の Get メソッドとプロパティを使用して Set メソッド**です。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**プロパティとメソッドを置き換える**プレビュー ウィンドウからです。 Set メソッドがあれば、変換することも、Set メソッドこの時点でを選択して**置換の Get メソッドとプロパティを使用して Set メソッド**です。

1. コードのプレビューの変更に満足したら場合、キーを押して**Enter**またはメニューから修正プログラムをクリックして、変更がコミットされます。

例:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>プロパティを Get メソッドに変換します。
**新機能:**プロパティを Get メソッドに変換することができます

****複数の直後に設定し、値を取得するプロパティがあります。 

**どう：**

1. Get メソッド名にカーソルを置きます。

1. 次に、次のいずれかの操作を行います。
   * **キーボード**
     * キーを押して**Ctrl + です。** トリガーに、**クイック アクションとリファクタリング**メニュー**メソッドとプロパティを置換する**プレビュー ウィンドウのポップアップからです。
   * **マウス**
     * コードを右クリックし、選択、**クイック アクションとリファクタリング**メニュー**メソッドとプロパティを置換する**プレビュー ウィンドウのポップアップからです。

1. コードのプレビューの変更に満足したら場合、キーを押して**Enter**またはメニューから修正プログラムをクリックして、変更がコミットされます。

## <a name="see-also"></a>参照  
[リファクタリング (C#)](../refactoring-csharp.md)  
[変更のプレビュー](../../ide/preview-changes.md)