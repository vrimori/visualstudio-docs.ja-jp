---
title: "エンコーディングと改行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "エディター, 改行"
  - "エンコーディング"
  - "改行文字"
  - "改行"
  - "Visual Studio, エンコーディング"
  - "Visual Studio, 改行文字"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# エンコーディングと改行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio では、\[ファイル\] メニューの **\[保存オプションの詳細設定\]** を使用して、必要な改行の種類を決定できます。  また、同じ設定でファイルのエンコーディングを変更することもできます。  
  
> [!NOTE]
>  開発設定の種類によっては \(Visual Basic、F\#、Web 開発\)、メニューに **\[保存オプションの詳細設定\]** が表示されない場合があります。  設定を \(たとえば \[全般\] に\) 変更するには、**\[ツール\]** から \[設定のインポートとエクスポート\] を開きます。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 Visual Studio では、次の文字が改行として解釈されます。  
  
-   CRLF: キャリッジ リターン文字とライン フィード文字 \(Unicode 文字では 000D \+ 000A\)  
  
-   LF: ライン フィード文字 \(Unicode 文字では 000A\)  
  
-   NEL: 次行記号 \(Unicode 文字では 0085\)  
  
-   LS: 行区切り記号 \(Unicode 文字では 2028\)  
  
-   PS: 段落区切り記号 \(Unicode 文字では 2029\)  
  
 他のアプリケーションからコピーされたテキストでは、元のエンコーディングと改行文字が保持されます。  たとえば、メモ帳からテキストをコピーし、Visual Studio でテキスト ファイルに貼り付けた場合、貼り付けたテキストの設定は、メモ帳で使用していた設定と同じになります。  
  
 改行文字が異なるファイルを開くと、一致しない改行文字を正規化するかどうか、また、どの種類の改行を使用するかを確認するダイアログ ボックスが表示される場合があります。