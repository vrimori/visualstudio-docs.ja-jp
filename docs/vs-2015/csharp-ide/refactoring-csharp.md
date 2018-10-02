---
title: リファクタリング (c#) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e74b540808c07aba5211ab69ea8270f6000b2a19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546551"
---
# <a name="refactoring-c"></a>リファクタリング (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

リファクタリングは、プロセスが、コードの外部の動作を変更することがなく、コードの内部構造を変更することによって書き込まれた後に、コードを向上させるのです。  
  
 Visual c# のリファクタリングの次のコマンドを提供する、**リファクタリング**メニュー。  
  
-   [メソッドの抽出リファクタリング (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [名前の変更リファクタリング (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [フィールドのカプセル化リファクタリング (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [インターフェイスの抽出リファクタリング (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [パラメーターの削除リファクタリング (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [パラメーター順序の再変更リファクタリング (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>複数プロジェクトのリファクタリング  
 Visual Studio では、複数のプロジェクトが同じソリューション内にあるプロジェクトのリファクタリングをサポートします。 すべてのファイル間での参照を修正、リファクタリング操作は、同じ言語のすべてのプロジェクト間でこれらの参照を修正します。 これは、すべてのプロジェクト間参照に対して機能します。 たとえば、クラス ライブラリ型の名前を変更するときに、クラス ライブラリを参照するコンソール アプリケーションがある場合 (を使用して、`Rename`リファクタリング操作)、コンソール アプリケーションでは、クラス ライブラリ型への参照も更新されます。  
  
## <a name="changes-preview"></a>変更のプレビュー  
 多くのリファクタリング操作は、それらの変更をコミットする前に、コードのリファクタリング操作を実行するすべての参照の変更を確認するための機会を提供します。 リファクタリング操作では、これらを**参照の変更をプレビュー**  ダイアログ ボックスでリファクタリング オプションが表示されます。 そのオプションを選択し、リファクタリング操作に同意した後、**プレビューの変更 ダイアログ ボックス**が表示されます。 なお、**変更のプレビュー**  ダイアログ ボックスが 2 つのビュー。 下のビュー、リファクタリング操作によりすべての参照の更新でのコードが表示されます。 キーを押して**キャンセル**上、**変更のプレビュー**  ダイアログ ボックスは、リファクタリング操作を停止しをコードに変更は加えられません。  
  
## <a name="refactoring-warnings"></a>リファクタリングの警告  
 コンパイラには、プログラムの詳細についてはありませんが、リファクタリングのエンジンがすべての適切な参照を更新できなかった可能性が考えられる場合は、警告ダイアログ ボックスが表示されます。 この警告ダイアログ ボックスでコードをプレビューする機会が得、**変更のプレビュー**変更をコミットする前に ダイアログ ボックス。  
  
> [!NOTE]
>  メソッドに構文エラー (を IDE では、赤い波線の下線で示す) が含まれている場合、リファクタリングのエンジンにはそのメソッド内の要素への参照項目更新されません。 次の例では、この動作を示します。  
  
 既定を実行する場合、リファクタリング操作の参照をプレビューすることがなく変更プログラムでは、コンパイル エラーが検出されたし、開発環境には、この警告ダイアログ ボックスが表示されます。  
  
 持つリファクタリング操作を実行する場合**参照の変更のプレビュー**し、有効で、プログラムでは、コンパイル エラーが検出されると、開発環境の下部にある次の警告メッセージが表示されます、**変更のプレビュー**ダイアログ ボックスで、表示する代わりに、**リファクタリングの警告** ダイアログ ボックス。  
  
 **プロジェクトまたはその依存関係のいずれかが現在ビルドしません。参照を更新できない可能性があります。**  
  
 このリファクタリングの警告はリファクタリングを提供する操作のみ、**参照の変更のプレビュー**オプション。  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>エラー トレラントなリファクタリングと検証結果  
 リファクタリングは、エラー トレラントです。 つまり、ビルドできないプロジェクトでのリファクタリングを行うことができます。 ただし、このような場合、リファクタリングのプロセスが正しく更新されないあいまいな参照。  
  
 **検証結果** ダイアログ ボックスで通知する場合は、リファクタリングのエンジンのコンパイル エラーを検出またはリファクタリング操作は、バインドが別のものへの参照をコードを誤って原因を検出しますもともと (問題を再バインド) にバインドされます。  
  
 有効にする、検証結果機能、**ツール** メニューのをクリックして**オプション**します。 **オプション** ダイアログ ボックスで、展開**テキスト エディター**、順に展開**c#** します。 クリックして **[詳細設定]** を選択し、**リファクタリングの結果を確認**チェック ボックスをオンします。  
  
 **検証結果** ダイアログ ボックスが 2 つの種類の問題を再バインドの違いを区別します。  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>参照の定義は、名前が変更されたシンボルにしなくなります。  
 このような再バインドの問題では、参照が不要になった名前が変更されたシンボルを参照するときに発生します。 次に例を示します。  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 名前を変更するリファクタリングを使用する場合`a`に`b`、このダイアログ ボックスが表示されます。 名前が変更された変数への参照を`a`フィールドへのバインドではなく、コンス トラクターに渡されるパラメーターにバインドするようになりました。  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>その定義になった名前が変更されたシンボル参照  
 このような再バインドの問題では、以前しなかった参照しない名前を変更したシンボルに今すぐ参照は名前が変更されたシンボルを参照しているときに発生します。 次に例を示します。  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 名前を変更するリファクタリングを使用する場合`OtherMethod`に`Method`、このダイアログ ボックスが表示されます。 内の参照`Main`を受け取るオーバー ロードされたメソッドを参照しています、`int`パラメーターを受け取るオーバー ロードされたメソッドではなく、`object`パラメーター。  
  
## <a name="see-also"></a>関連項目  
 [C#、Visual Studio 開発環境を使用します。](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [方法 : C# リファクタリング スニペットを復元する](../ide/how-to-restore-csharp-refactoring-snippets.md)