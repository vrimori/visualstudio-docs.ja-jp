---
title: ワークフロー デザイナーを参照して .NET の種類 ダイアログ ボックスを選択
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4d136c98acd2719abd07f8feb2f9def48ec6b2ec
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973916"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>[.NET 型の参照と選択] ダイアログ ボックス

**プロパティ**ウィンドウ、ダイアログ ボックス、またはを選択すると、変数デザイナーなどのデザイナー**型を参照しています.** データ型の一覧からは、**を参照して .NET 型を選択** ダイアログ ボックス (「型ブラウザー」と省略形で呼ばれます)。 このダイアログ ボックスでは、アセンブリとプロジェクトのツリー表示から型を選択できます。

 このダイアログ ボックスは、次のようなさまざなユーザー シナリオで使用されます。

-   変数または引数の型を設定する。

-   一般的なアクティビティの型を選択する。

-   <xref:System.Activities.Statements.TryCatch> アクティビティに catch を追加する。

> [!NOTE]
> 型ブラウザーは、多次元配列型ではなく Visual Basic ジャグ配列型を表示できます。 参照してください[ジャグ配列](http://go.microsoft.com/fwlink/?LinkId=195226)と[多次元配列](http://go.microsoft.com/fwlink/?LinkId=195227)詳細についてはします。

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>型ブラウザーでの値型または参照型の選択

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>型ブラウザーで値型または参照型を選択するには

1.  **型名**ボックスを使用する型の名前を入力します。

2.  次のいずれかの操作を行います。

    -   ツリーに使用する型の名前が表示されたら、**型名**ボックスをオンにする型をダブルクリックします。

    -   ための十分な文字を入力して、**型名**ボックスを使用して、enter キーを押し、種類を選択する型を一意に識別するには

### <a name="to-select-a-generic-type-from-the-type-browser"></a>型ブラウザーでジェネリック型を選択するには

1.  **型名**ボックスで使用する型の名前を入力します。

2.  ツリーに使用する型の名前が表示されたら、**型名**ボックスで、表示により、ドロップ ダウン ボックスをオンにする をクリックします。

     ドロップダウン ボックスから、ジェネリックを閉じ をクリックしを使用する場合の種類を選択**OK**です。

## <a name="types-displayed-in-the-type-browser"></a>型ブラウザーに表示される型
 型ブラウザーに表示される型は、型ブラウザーを起動した方法に応じて変わる場合があります。 内のワークフロー プロジェクトから型ブラウザーを起動したかどうかは**vs2010**、既定ですべての参照されたアセンブリで型および参照先のプロジェクトが表示されます。 外部から型ブラウザーを起動した場合、 **vs2010**プロジェクト (このような再ホストされたワークフロー アプリケーションやスタンドアロンのワークフロー ファイル)、システムの既定ではすべての AppDomain に読み込まれたアセンブリから型を表示し、.

 アクティビティ デザイナーの開発者は、型ブラウザーの型をフィルター処理できます。 どのアクティビティでも、表示されるのは型のサブセットのみです。 たとえば、<xref:System.Activities.Statements.TryCatch> アクティビティでは、<xref:System.Exception> から派生した型のみが型ブラウザーに表示されます。

## <a name="filtering-search-results-in-the-type-browser"></a>型ブラウザーでの検索結果のフィルター処理
 内の型の一覧、**型名**ボックスが一致するものを検索する文字を入力するように短くを取得します。 フィルター処理された一覧には、入力した文字列で完全修飾名が始まる型、または、入力した文字列で始まる短い名前を持つ型のみが表示されます。

 例えば:

1.  入力**操作**と一致する<xref:System.OperationCanceledException>ではなく<xref:System.InvalidOperationException>です。 <xref:System.InvalidOperationException> と一致するためには、「System.I」または「Invalid」と入力します。

2.  入力**ジェネリック**と一致する<xref:System.GenericUriParser>でない型しますが、<xref:System.Collections.Generic>名前空間。 <xref:System.Collections.Generic> 名前空間の型を検索するには、その名前空間の完全修飾名を入力します。

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>型ブラウザー ダイアログを使用したサービス コントラクトの選択
 サービス コントラクト型を選択すると、型ブラウザーは <xref:System.ServiceModel.ServiceContractAttribute> 属性を持つ型だけを表示します。

## <a name="see-also"></a>関連項目

- [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)