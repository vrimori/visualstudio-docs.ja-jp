---
title: "エラー : ローカル コンピューターのファイアウォール | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# エラー : ローカル コンピューターのファイアウォール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio を実行するローカル コンピューターのインターネット接続ファイアウォールは、リモート デバッグを許可するように設定されていません。  既定のトランスポートを使用したマネージ リモート デバッグまたはネイティブ リモート デバッグでは、DCOM トラフィック用に TCP 135 ポートを開く必要があります。  ファイルおよびプリンターの共有を有効にし、devenv.exe を例外リストに追加することも必要です。  また、IPSEC ポートを開く必要がある場合もあります。  
  
 詳細については、「[デバイスのリモート ツールのセットアップ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)」を参照してください。