---
title: FxCopCmd エラー |Microsoft ドキュメント
ms.date: 10/19/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b407167a772a82b56c39ba222dc3c1f563f5c012
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd ツールのエラー

FxCopCmd では、致命的なであるすべてのエラーは考慮されません。 FxCopCmd に部分的な分析を実行するための十分な情報がある場合は、分析およびレポートのエラーが発生したを実行します。 32 ビット整数である、エラー コードには、エラーに対応する数値の値のビットごとの組み合わせが含まれています。

次の表では、FxCopCmd によって返されるエラー コードについて説明します。

|Error|数値の値|
|-----------|-------------------|
|エラーのないです。|0x0|
|解析エラー|0x1|
|規則の例外|0x2|
|プロジェクトの読み込みエラー|0x4|
|アセンブリの読み込みエラー|0x8|
|ルール ライブラリの読み込みエラー|0x10|
|インポート レポートの読み込みエラー|0x20|
|出力エラー|0x40|
|コマンド ライン スイッチのエラー|0x80|
|初期化エラー|0x100|
|アセンブリ参照エラー|0x200|
|BuildBreakingMessage|0x400|
|不明なエラー|0x1000000|

**解析エラー**致命的なエラーが返されます。 分析が完了しないことを示します。 該当する場合、エラー コードには、致命的なエラーの根本原因も含まれます。 次の条件は、致命的なエラーを生成します。

- 入力の不足のため、分析を実行できませんでした。

- 分析には、FxCopCmd によって処理されていない例外がスローされました。

- 指定したプロジェクト ファイルでは、見つからなかったか、壊れています。

- 出力オプションが指定されていないか、ファイルに書き込めませんでした。

> [!NOTE]
> FxCopCmd のリターン コード**アセンブリ参照エラー** 0x200 自体がエラーではなく、警告します。 このリターン コードは、FxCopCmd がそれらを処理することが、そのことが存在していないの間接参照を示します。 警告は、一部の分析結果が侵害されている可能性があることを意味します。 扱う**アセンブリ参照エラー**他のリターン コードと組み合わせると、エラーとして。

## <a name="see-also"></a>関連項目

- [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)