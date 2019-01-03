---
title: Modeling SDK for Visual Studio - ドメイン固有言語
titleSuffix: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9524e071edc82ba2da78df77afdda85e0ac10505
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860336"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modeling SDK for Visual Studio - ドメイン固有言語

Modeling SDK for Visual Studio を使用して、Visual Studio に統合できる強力なモデル ベースの開発ツールを作成できます。 同様に、1 つ以上のモデル定義を作成して、一連のツールと統合できます。

MSDK の中核は、業務分野の概念を表すために作成するモデルの定義です。 図式ビュー、コードとその他の成果物で、モデルに変換するため、コマンドを生成する機能、およびコードおよび Visual Studio の他のオブジェクトと対話する機能などのツールのさまざまなモデルを囲むことができます。 モデルを開発するとき、他のモデルやツールと組み合わせて、開発の中央に配置される強力なツール セットを形成することができます。

MSDK では、ドメイン固有言語 (DSL) の形式でモデルを迅速に開発できます。 グラフィカルな表記と共にスキーマまたは抽象構文を定義する専用のエディターを使用することから始めます。 この定義から、VMSDK は次を生成します。

- トランザクション ベースのストアで実行する厳密に型指定された API によるモデル実装。

- ツリー ベースのエクスプローラー。

- 定義するモデルまたは一部をユーザーが表示できるグラフィカル エディター。

- 読み取り可能な XML にモデルを保存するシリアル化メソッド。

- テキスト テンプレートを使用して、プログラム コードとその他の成果物を生成するための機能。

これらのすべての機能をカスタマイズおよび拡張できます。 拡張した機能は、統合後も DSL 定義を更新でき、拡張した機能を失うことなく機能を再生成できるように統合されています。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[関連するブログの投稿](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

高度な技法とトラブルシューティングに関するガイダンスについては、次を参照してください。 [Visual Studio DSL & Modeling Tools 機能拡張フォーラム](http://go.microsoft.com/fwlink/?LinkID=186074)します。

## <a name="in-this-section"></a>このセクションの内容
 [ドメイン固有言語の概要](../modeling/getting-started-with-domain-specific-languages.md)

 [モデル、クラス、およびリレーションシップについて](../modeling/understanding-models-classes-and-relationships.md)

 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)

 [ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)

 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [ドメイン固有言語からのコード生成](../modeling/generating-code-from-a-domain-specific-language.md)

 [DSL コードについて](../modeling/understanding-the-dsl-code.md)

 [ファイル格納処理および XML シリアル化処理のカスタマイズ](../modeling/customizing-file-storage-and-xml-serialization.md)

 [ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)

 [Windows フォームに基づくドメイン固有言語の作成](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [WPF に基づくドメイン固有言語の作成](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [方法: ドメイン固有言語デザイナーを拡張します。](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Visualization and Modeling SDK に対してサポートされている Visual Studio のエディション](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [方法: ドメイン固有言語を新しいバージョンに移行します。](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Modeling SDK for Visual Studio の API リファレンス](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
