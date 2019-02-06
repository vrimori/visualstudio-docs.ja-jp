---
title: T4 テキスト変換のカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bc59718131cc4879a351097b767fa513d72b5c81
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962755"
---
# <a name="customize-t4-text-transformation"></a>T4 テキスト変換をカスタマイズする

テキスト テンプレートは、変換プロセスを通して、プログラム コードまたはその他のテキスト ファイルを生成するための Visual Studio の機能です。 [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] を使用して、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることで、既定のテンプレートの変換プロセスを拡張することができます。

## <a name="in-this-section"></a>このセクションの内容

 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md) テキスト変換のしくみについて説明し、テンプレートのホストとディレクティブ プロセッサの役割について説明します。

 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサを作成する](../modeling/creating-custom-t4-text-template-directive-processors.md)などは、テンプレートのディレクティブを使用して、ディレクティブ プロセッサ`<#@template#>.`テンプレートのコンパイル時に実行され、アセンブリとその他のリソースを読み込むことができます。 実行時にリソースを読み込むコードを挿入することもできます。 ディレクティブ プロセッサを定義することでは、テンプレートの複雑さを軽減できます。

 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md) メニュー コマンドまたはイベント ハンドラーなどの Visual Studio 拡張機能を作成する場合、拡張機能が任意のテキスト テンプレートを変換するテキスト テンプレート サービスを使用できます。 セッション オブジェクトを使用して、テンプレートにパラメーターのデータを渡し、`<#@parameter#>` ディレクティブを使用して、テンプレート内から値を取得することができます。

 [カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md) テンプレートのコードを実行するとき、ホストは外部のファイルへのアクセスとアプリケーションの状態を提供します。 たとえば、Visual Studio 内でテキスト変換を実行するホストは、**ソリューション エクスプローラー**へのアクセスを提供します。 これは、エラーをエラー メッセージ ウィンドウに表示します。 別のコンテキストでテキスト変換を実行する場合は、そのコンテキストで使用可能なサービスへのアクセスを提供する独自のホストを定義できます。

 Visual Studio 拡張機能を作成する場合は、独自のホストを記述する代わりに既存のテキスト変換サービスの使用を検討してください。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。

## <a name="reference"></a>参照

- [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)は、テキスト テンプレートのディレクティブとコントロール ブロックの構文について説明します。