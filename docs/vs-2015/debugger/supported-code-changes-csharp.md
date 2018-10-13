---
title: サポートされるコードの変更 (c#) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02777efc206fed14c32a2cc73d31e475fd9e2064
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262566"
---
# <a name="supported-code-changes-c"></a>サポートされているコード変更 (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

エディット コンティニュでは、メソッドの本体内で行ったほとんどの種類のコード変更を処理できます。 しかし、メソッドの本体外で行った変更の大部分やメソッドの本体内で行った一部の変更は、デバッグ時に適用できません。 このようなサポートされていない変更を適用するには、デバッグを停止し、新しいバージョンのコードを再起動する必要があります。  
  
 デバッグ セッション中に C# コードに適用できない変更は、次のとおりです。  
  
-   現在のステートメントまたはその他のアクティブ ステートメントに対する変更。  
  
     アクティブ ステートメントには、現在のステートメントを取得するために呼び出される、呼び出し履歴上の関数内に存在するすべてのステートメントが含まれます。  
  
     ソース ウィンドウ内では、現在のステートメントは黄色の背景で示されます。 その他のアクティブ ステートメント (読み取り専用) は、網かけの背景で示されます。 これらの既定の色を変更することができます、**オプション** ダイアログ ボックス。  
  
-   型のシグネチャの変更  
  
-   以前にキャプチャされていない変数をキャプチャする匿名メソッドの追加。  
  
-   属性の追加、削除、変更。  
  
-   `using` ディレクティブの追加、削除、変更。  
  
-   アクティブ ステートメントの周囲への `foreach`、`using`、または `lock` の追加。  
  
## <a name="unsafe-code"></a>アンセーフ コード  
 アンセーフ コードを変更する場合、セーフ コードを変更するときと同じ制限に加えて、もう 1 つ追加の制限が適用されます。エディット コンティニュでは、`stackalloc` 演算子を含むメソッド内に存在するアンセーフ コードへの変更はサポートしていません。  
  
## <a name="exceptions"></a>例外  
 エディット コンティニュは、`catch` と `finally` ブロックへの変更をサポートしています。ただし、アクティブ ステートメントの周囲の `catch` または `finally` ブロックの追加は許可されていません。  
  
## <a name="unsupported-scenarios"></a>サポートされていないシナリオ  
 次のデバッグ シナリオでは、エディット コンティニュを使用できません。  
  
-   特定の状況での LINQ のコードをデバッグ。 詳しくは、「[LINQ のデバッグ](../debugger/debugging-linq.md)」をご覧ください。  
  
    -   以前にキャプチャされていない変数のキャプチャ。  
  
    -   クエリ式の型の変更 (たとえば、select a => select new { A = a };)  
  
    -   アクティブなステートメントを含む `where` の削除。  
  
    -   アクティブなステートメントを含む `let` の削除。  
  
    -   アクティブなステートメントを含む `join` の削除。  
  
    -   アクティブなステートメントを含む `orderby` の削除。  
  
-   混合モードでの (ネイティブ/マネージ) デバッグ  
  
-   SQL デバッグ  
  
-   ワトソン博士のダンプのデバッグ  
  
-   未処理の例外を後のコード編集時に、"**ハンドルされない例外でコール スタックをアンワインド**"オプションが選択されていません。  
  
-   埋め込まれたランタイム アプリケーションのデバッグ  
  
-   持つアプリケーションのデバッグ**にアタッチ**を選択して、アプリケーションを実行する代わりに**開始**から、**デバッグ**メニュー。  
  
-   最適化されたコードのデバッグ  
  
-   ビルド エラーによって新しいバージョンのビルドが失敗した後の旧バージョンのデバッグ  
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [方法 : エディット コンティニュを使用する (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)



