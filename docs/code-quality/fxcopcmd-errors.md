---
title: FxCopCmd エラー
ms.date: 10/19/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 34ec1b04e10b874d6f8373b5eb0e6c2e5c6d70e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844081"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd ツールのエラー

FxCopCmd に致命的なエラーをすべてを考慮しません。 FxCopCmd に部分的な分析を実行するための十分な情報がある場合は、発生した分析とレポートのエラーを実行します。 32 ビット整数である、エラー コードには、エラーに対応する数値の値のビットごとの組み合わせが含まれています。

次の表では、FxCopCmd によって返されるエラー コードについて説明します。

|Error|数値|
|-----------|-------------------|
|エラーなし|0x0|
|分析エラー|0x1|
|規則の例外|0x2|
|プロジェクトの読み込みエラー|0x4|
|アセンブリの読み込みエラー|0x8|
|規則ライブラリの読み込みエラー|0x10|
|インポートのレポートの読み込みエラー|0x20|
|出力エラー|0x40|
|コマンド ライン スイッチのエラー|0x80|
|初期化エラー|0x100|
|アセンブリ参照エラー|0x200|
|BuildBreakingMessage|0x400|
|不明なエラー|0x1000000|

**分析エラー**致命的なエラーが返されます。 それでも、分析を完了できませんでした。 該当する場合、エラー コードには、致命的なエラーの根本原因も含まれています。 次の条件は、致命的なエラーを生成します。

- 入力の不足のため、分析を実行できませんでした。

- 分析には、FxCopCmd によって処理されない例外がスローされました。

- 指定したプロジェクト ファイルが見つかりませんでしたか壊れています。

- 出力オプションが指定されなかったか、ファイルを書き込めませんでした。

> [!NOTE]
> FxCopCmd のリターン コード**アセンブリ参照エラー** 0x200 自体がエラーではなく警告です。 このリターン コードは、FxCopCmd がそれらを処理することがないの間接参照を示します。 警告は、一部の分析結果が侵害されている可能性があることを意味します。 扱う**アセンブリ参照エラー**他のリターン コードと組み合わせると、エラーとして。

## <a name="see-also"></a>関連項目

- [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)