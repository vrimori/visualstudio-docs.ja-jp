---
title: "Visual Studio での Get メソッドのプロパティへの変換、およびプロパティの Get メソッドへの変換 | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 3d0a532e2e3e5bb8afa4a3c3dc9720134a1b7e8b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get メソッドのプロパティへの変換/プロパティの Get メソッドへの変換リファクタリング

これらのリファクタリングは以下に適用されます。

- C#

## <a name="convert-get-method-to-property"></a>Get メソッドのプロパティへの変換

**機能:** Get メソッド (必要に応じて Set メソッド) をプロパティ に変換できます。その逆もできます。

**条件:** ロジックを含まない Get メソッドがあるとき。

### <a name="how-to"></a>方法

1. Get メソッド名にカーソルを置きます。

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[Replace method with property]\(メソッドをプロパティに置換\)** を選択します。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[Replace method with property]\(メソッドをプロパティに置換\)** を選択します。

1. (省略可能) Set メソッドがある場合、このときに **[Replace Get method and Set method with property]\(Get メソッドと Set メソッドをプロパティに置換\)** を選択して Set メソッドも変換できます。

1. コード プレビューで変更を確認したら、**Enter** キーを押すか、メニューから [修正] をクリックすると、変更がコミットされます。

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

## <a name="convert-property-to-get-method"></a>プロパティの Get メソッドへの変換

**機能:** プロパティを Get メソッドに変換できます。

**条件:** 値の設定や取得をするだけではないプロパティがあるとき。 

### <a name="how-to"></a>方法

1. Get メソッド名にカーソルを置きます。

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[Replace property with method]\(プロパティをメソッドに置換\)** を選択します。
   - **マウス**
     - コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[Replace property with methods]\(プロパティをメソッドに置換\)** を選択します。

1. コード プレビューで変更を確認したら、**Enter** キーを押すか、メニューから [修正] をクリックすると、変更がコミットされます。

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)