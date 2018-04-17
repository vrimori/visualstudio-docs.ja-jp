---
title: サポートされるコード変更 (c# および Visual Basic) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/11/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: eba3de7930b650ad7c1fc2d6ad4511ca3ca4c9d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supported-code-changes-c-and-visual-basic"></a>サポートされているコード変更 (c# および Visual Basic)
エディット コンティニュでは、メソッドの本体内で行ったほとんどの種類のコード変更を処理できます。 しかし、メソッドの本体外で行った変更の大部分やメソッドの本体内で行った一部の変更は、デバッグ時に適用できません。 このようなサポートされていない変更を適用するには、デバッグを停止し、新しいバージョンのコードを再起動する必要があります。

## <a name="supported-changes-to-code"></a>サポートされているコード変更

次の表では、設定可能な c# および Visual Basic コードをデバッグ セッション中に、セッションを再起動しなくても変更が表示されます。

|言語要素/機能|サポートされている編集操作|制限事項|
|-|-|-|
|種類|メソッド、フィールド、コンス トラクター、他を追加します。|[はい](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|追加または変更|×|
|async と await 式|追加または変更|[はい](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|動的オブジェクト|追加または変更|×|
|ラムダ式|追加または変更|[はい](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 式|追加または変更|[ラムダ式と同じ](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> エディット コンティニュでは、文字列の補間と null 条件演算子などの新しい言語機能はサポートされて一般にします。 最新情報については、次を参照してください。、 [Enc サポート編集](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)ページ。

## <a name="unsupported-changes-to-code"></a>コードにサポートされていない変更
 次の変更は、デバッグ セッション中に、c# および Visual Basic のコードに適用できません。  
  
-   現在のステートメントまたはその他のアクティブ ステートメントに対する変更。  
  
     アクティブ ステートメントには、現在のステートメントを取得するために呼び出される、呼び出し履歴上の関数内に存在するすべてのステートメントが含まれます。  
  
     ソース ウィンドウ内では、現在のステートメントは黄色の背景で示されます。 その他のアクティブ ステートメント (読み取り専用) は、網かけの背景で示されます。 変更できます。 これらの既定の色、**オプション** ダイアログ ボックス。

- 次の表は、言語要素によってコードにサポートされていない変更を示します。

|言語要素/機能|サポートされていない編集操作|
|-|-|
|すべてのコード要素|名前の変更|
|名前空間|追加|
|名前空間、型、メンバー|削除|
|ジェネリック|追加または変更|
|インターフェイス|変更|
|種類|抽象または仮想メンバーを追加、上書きを追加 (を参照してください[詳細](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|種類|デストラクターを追加します。|
|メンバー|埋め込み相互運用機能型を参照するメンバーを変更します。|
|メンバー (Visual Basic)|On Error または Resume ステートメントを使用してメンバーを変更します。|
|メンバー (Visual Basic)|集計、Group By、単純な結合またはグループに参加 LINQ のクエリ句を含むメンバーを変更します。|
|メソッド|署名を変更します。|
|メソッド|メソッド本体を追加することで、抽象メソッドになる非抽象の作成します。|
|メソッド|メソッドの本体を削除します。|
|属性|追加または変更|
|イベントまたはプロパティ|変更が型パラメーター、基本データ型、デリゲート型、または型を返す |
|演算子またはインデクサー|変更が型パラメーター、基本データ型、デリゲート型、または型を返す |
|catch ブロック|アクティブなステートメントが含まれているときに変更します。|
|try – catch – finally ブロック|アクティブなステートメントが含まれているときに変更します。|
|using ステートメント|追加|
|非同期のメソッドまたはラムダ|.NET Framework 4 を対象とするプロジェクトで非同期のメソッドまたはラムダを変更し、削減 (を参照してください[詳細](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|.NET Framework 4 を対象とするプロジェクトで、反復子を変更し、削減 (を参照してください[詳細](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>アンセーフ コード  
 アンセーフ コードを変更する場合、セーフ コードを変更するときと同じ制限に加えて、もう 1 つ追加の制限が適用されます。エディット コンティニュでは、`stackalloc` 演算子を含むメソッド内に存在するアンセーフ コードへの変更はサポートしていません。  

## <a name="unsupported-app-scenarios"></a>サポートされていないアプリ シナリオ

サポートされていないアプリとプラットフォームには、ASP.NET 5、Silverlight 5、および Windows 8.1 が含まれます。

> [!NOTE]
> サポートされているアプリは、Windows 10、および .NET Framework 4.6 を対象とする x86 および x64 のアプリで UWP を含める (.NET Framework は、デスクトップのバージョンのみ) デスクトップまたはそれ以降のバージョン。
  
## <a name="unsupported-scenarios"></a>サポートされていないシナリオ  
 次のデバッグ シナリオでは、エディット コンティニュを使用できません。  
  
-   混合モードでの (ネイティブ/マネージ) デバッグ  
  
-   SQL デバッグ  
  
-   ワトソン博士のダンプのデバッグ  
  
-   埋め込まれたランタイム アプリケーションのデバッグ  
  
-   プロセスにアタッチを使用して、アプリケーションのデバッグ (**デバッグ > プロセスにアタッチする**) を選択して、アプリケーションを実行することがなく**開始**から、**デバッグ**メニュー。  
  
-   最適化されたコードのデバッグ  
  
-   ビルド エラーによって新しいバージョンのビルドが失敗した後の旧バージョンのデバッグ
  
## <a name="see-also"></a>関連項目  
 [エディット コンティニュ (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [方法 : エディット コンティニュを使用する (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)