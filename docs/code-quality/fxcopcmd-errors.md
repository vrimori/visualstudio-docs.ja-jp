---
title: "FxCopCmd エラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.openlocfilehash: 2439b04c921de6e06b98bd1bb5a9fc0af3ea56d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd エラー
FxCopCmd では、致命的なであるすべてのエラーは考慮されません。 FxCopCmd に部分的な分析を実行するための十分な情報がある場合は、分析およびレポートのエラーが発生したを実行します。 32 ビット整数である、エラー コードには、エラーに対応する数値の値のビットごとの組み合わせが含まれています。  
  
 次の表では、FxCopCmd によって返されるエラー コードについて説明します。  
  
|エラー|数値の値|  
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
  
 致命的なエラーに対しては、解析エラーが返されます。 分析が完了しないことを示します。 該当する場合、エラー コードには、致命的なエラーの根本原因も含まれます。 次の条件は、致命的なエラーを生成します。  
  
-   解析できませんでした入力の不足によって発生したものです。  
  
-   分析には、FxCopCmd によって処理されていない例外がスローされました。  
  
-   指定したプロジェクト ファイルでは、見つからなかったか、壊れています。  
  
-   出力オプションが指定されていないか、ファイルに書き込めませんでした。  
  
    > [!NOTE]
    >  FxCopCmd リターン コード「アセンブリ参照エラー」0x200 自体がエラーではなく、警告します。 このリターン コードは、不明な間接参照が見つかりましたが、FxCopCmd がそれらの処理できたことを示します。 一部の分析結果が侵害されている可能性があることを警告することをお勧めします。 他のリターン コードと結合されているときに、エラーとしてリターン コードの「アセンブリは、エラーを参照」を検討してください。  
  
## <a name="see-also"></a>関連項目  
 [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)