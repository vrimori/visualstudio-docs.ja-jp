---
title: FxCopCmd エラー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: douge
ms.openlocfilehash: 828805e0746fb985ea310b755cdaaa252e215a07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751715"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd エラー
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
  
 解析エラーでは、致命的なエラーが返されます。 それでも、分析を完了できませんでした。 該当する場合、エラー コードには、致命的なエラーの根本原因も含まれています。 次の条件は、致命的なエラーを生成します。  
  
-   解析できませんでした入力の不足によって発生したものです。  
  
-   分析には、FxCopCmd によって処理されない例外がスローされました。  
  
-   指定したプロジェクト ファイルが見つかりませんでしたか壊れています。  
  
-   出力オプションが指定されなかったか、ファイルを書き込めませんでした。  
  
    > [!NOTE]
    >  FxCopCmd リターン コード「アセンブリ参照エラー」0x200 自体がエラーではなく警告です。 このリターン コードでは、不明な間接参照が見つかりましたが、FxCopCmd がそれらを処理できないことを示します。 一部の分析結果が侵害されている可能性があることを警告することをお勧めします。 他のリターン コードと結合されているときにエラーとしてリターン コードの「アセンブリ参照エラー」を検討してください。  
  
## <a name="see-also"></a>関連項目  
 [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)