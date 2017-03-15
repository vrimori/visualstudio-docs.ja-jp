---
title: "FxCopCmd エラー | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd エラー"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# FxCopCmd エラー
FxCopCmd は、すべてのエラーを致命的と見なすわけではありません。  FxCopCmd に部分的な分析を実行できるだけの十分な情報がある場合、FxCopCmd は部分的な分析を実行し、発生したエラーを報告します。  32 ビット整数のエラー コードには、エラーに対応する数値のビットごとの組み合わせが含まれます。  
  
 次の表に、FxCopCmd が返すエラー コードを示します。  
  
|エラー|数値|  
|---------|--------|  
|エラーなし|0x0|  
|分析エラー|0x1|  
|規則例外|0x2|  
|プロジェクト読み込みエラー|0x4|  
|アセンブリ読み込みエラー|0x8|  
|規則ライブラリ読み込みエラー|0x10|  
|インポート レポート読み込みエラー|0x20|  
|出力エラー|0x40|  
|コマンド ライン スイッチ エラー|0x80|  
|初期化エラーです。|0x100|  
|アセンブリ参照エラー|0x200|  
|BuildBreakingMessage|0x400|  
|不明なエラー|0x1000000|  
  
 分析エラーは、エラーが致命的である場合に返されます。  このエラーは分析を完了できなかったことを示します。  場合によっては、エラー コードには致命的なエラーの根本的な原因も含まれています。  致命的なエラーは次の場合に生成されます。  
  
-   入力の不足により、分析を実行できなかった。  
  
-   分析中に FxCopCmd が処理できない例外がスローされた。  
  
-   指定されたプロジェクト ファイルが見つからないか、破損している。  
  
-   出力オプションが指定されていないか、ファイルを書き込むことができなかった。  
  
    > [!NOTE]
    >  FxCopCmd のリターン コード "アセンブリ参照エラー" 0x200 自体はエラーではなく警告です。  このリターン コードは、不明な間接参照が見つかったが、FxCopCmd でそれらを処理できたことを示します。  一部の分析結果が正しくない可能性があるという警告です。  "アセンブリ参照エラー" リターン コードは、他のリターン コードと組み合わせてエラーと見なします。  
  
## 参照  
 [コード分析のアプリケーション エラー](../code-quality/code-analysis-application-errors.md)