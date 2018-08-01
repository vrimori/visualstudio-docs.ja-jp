---
title: T4 テキスト変換のカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7755444781bb0205e7483e2365d80cac909c62c6
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380104"
---
# <a name="customize-t4-text-transformation"></a>T4 テキスト変換をカスタマイズする

テキスト テンプレートは、プログラム コードまたは変換プロセスには、その他のテキスト ファイルを生成するための Visual Studio の機能です。 使用して[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることで、既定のテンプレートの変換プロセスを拡張することができます。

## <a name="in-this-section"></a>このセクションの内容

 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)テキスト変換のしくみについて説明しますと、テンプレートのホストとディレクティブ プロセッサの役割について説明します。

 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサを作成する](../modeling/creating-custom-t4-text-template-directive-processors.md)などは、テンプレートのディレクティブを使用して、ディレクティブ プロセッサ`<#@template#>.`テンプレートのコンパイル時に実行され、アセンブリとその他のリソースを読み込むことができます。 実行時にリソースを読み込むコードを挿入することもできます。 ディレクティブ プロセッサを定義することでは、テンプレートの複雑さを軽減できます。

 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)メニュー コマンドまたはイベント ハンドラーなどの Visual Studio 拡張機能を作成する場合、拡張機能が任意のテキスト テンプレートを変換するテキスト テンプレート サービスを使用できます。 セッション オブジェクトを使用して、テンプレートにパラメーターのデータを渡すし、を使用して、テンプレート内から値を取得することができます、`<#@parameter#>`ディレクティブ。

 [カスタム ホストを使用してテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)ホストが外部のファイルとアプリケーションの状態へのアクセスを提供するテキスト テンプレートのコードを実行するとします。 たとえば、Visual Studio でテキスト変換を実行するホストにアクセスできるように**ソリューション エクスプ ローラー**します。 エラーは、エラー メッセージ ウィンドウにも表示されます。 別のコンテキストでテキスト変換を実行する場合は、そのコンテキストで使用可能なサービスへのアクセスを提供する、独自のホストを定義できます。

 Visual Studio 拡張機能を作成する場合は、独自のホストを記述する代わりに既存のテキスト変換サービスの使用を検討してください。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。

## <a name="reference"></a>参照

- [T4 テキスト テンプレートを記述](../modeling/writing-a-t4-text-template.md)テキスト テンプレートのディレクティブとコントロール ブロックの構文について説明します。