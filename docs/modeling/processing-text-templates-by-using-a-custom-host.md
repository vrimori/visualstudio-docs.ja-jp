---
title: カスタム ホストを使用したテキスト テンプレートの処理
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d6de5da0ca6026ad993cbd2d4b2e9cb3e8c9280b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962002"
---
# <a name="process-text-templates-by-using-a-custom-host"></a>カスタム ホストを使用してテキスト テンプレートを処理する

*テキスト テンプレート変換*処理は、*テキスト テンプレート*ファイルとして入力し、テキスト ファイルを出力として生成します。 テキスト変換エンジンは、Visual Studio の拡張機能、または Visual Studio がインストールされているマシンで実行されているスタンドアロンのアプリケーションから呼び出すことができます。 ただし、提供する必要があります、*テキスト テンプレート ホスト*します。 このクラスは、テンプレートを環境に接続し、アセンブリやインクルード ファイルなどのリソースの検索と、出力およびエラー メッセージの処理を行います。

> [!TIP]
> パッケージまたは Visual Studio 内で実行される拡張機能を記述する場合は、独自のホストを記述する代わりに、テキスト テンプレート サービスを使用することを検討します。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。

> [!NOTE]
> サーバー アプリケーションでテキスト テンプレート変換を使用することはお勧めしません。 また、シングル スレッド以外でテキスト テンプレート変換を使用することはお勧めしません。 テキスト テンプレート エンジンでは、単一の AppDomain を再利用して、テンプレートを変換、コンパイル、および実行するためです。 変換されたコードは、スレッド セーフになるように設計されているわけではありません。 エンジンが順番に処理するファイル、デザイン時に Visual Studio プロジェクトでは設計されています。
>
> 実行時のアプリケーションでは、前処理されたテキスト テンプレートの使用を検討してください。 を参照してください[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)します。

コンパイル時に決定されるテンプレートのセットをアプリケーションで使用する場合は、前処理されたテキスト テンプレートを使用する方が簡単です。 アプリケーションは、Visual Studio がインストールされていないコンピューターで実行される場合は、アプローチを使用することもできます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="execute-a-text-template-in-your-application"></a>テキスト テンプレートをアプリケーションを実行します。

テキスト テンプレートを実行するには、<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> の ProcessTemplate メソッドを呼び出します。

```csharp
using Microsoft.VisualStudio.TextTemplating;
...
Engine engine = new Engine();
string output = engine.ProcessTemplate(templateString, host);
```

 アプリケーションでは、テンプレートを見つけて提供すると共に、出力を処理する必要があります。

 `host` パラメーターでは、<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> を実装するクラスを指定する必要があります。 これはエンジンによってコールバックされます。

 ホストは、エラーのログ記録、アセンブリとインクルード ファイルへの参照の解決、テンプレートを実行できるアプリケーション ドメインの指定、各ディレクティブの適切なプロセッサの呼び出しを実行できる必要があります。

 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> 定義されている**Microsoft.VisualStudio.TextTemplating。\*します。0 dll**、および<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>で定義されている**Microsoft.VisualStudio.TextTemplating.Interfaces。\*します。0 dll**します。

## <a name="in-this-section"></a>このセクションの内容
 [チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)Visual Studio の外部テキスト テンプレートの機能を利用できるようにするカスタム テキスト テンプレート ホストを作成する方法を示します。

## <a name="reference"></a>参照
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>

## <a name="related-sections"></a>関連項目

- [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)テキスト変換のしくみについて説明します、部分をカスタマイズできます。
- [カスタム T4 テキスト テンプレート ディレクティブ プロセッサを作成する](../modeling/creating-custom-t4-text-template-directive-processors.md)テンプレート ディレクティブ プロセッサのテキストの概要を説明します。