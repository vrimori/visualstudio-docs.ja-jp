---
title: "ポートのサプライヤーを実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] のデバッグ、ポート サプライヤーを実装します。"
  - "ポートの供給業者を実装します。"
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# ポートのサプライヤーを実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ セッションのマネージャー \(SDM\) にポートのサプライヤーの要求次第提供ポートです。  ポートの業者は新しいデバイスをサポートする必要がある場合DCOM マシンにデバッグ時または実行する必要があります。  たとえば携帯電話でデバッグを提供するために携帯電話に接続するポート \(IR またはセルの接続で使用\) や電話プログラムで実行されているプロセスを列挙するポートの業者を実行する場合があります。  
  
 Windows ベースのコンピューターでプログラムをデバッグするにはリモート デバッグ\)ネイティブなポートの業者を提供し共通言語ランタイム \(CLR\) ではこのため独自のポートの業者をこの場合実行する必要はありません。  
  
## このセクションの内容  
 [実装して、ポート サプライヤーを登録します。](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM がサプライヤーのポートとポートとやり取りする方法について説明します。  
  
 [必要なポート サプライヤー インターフェイス](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 ポートの業者を取得するために必要なインターフェイスについて説明します。  
  
## 関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグの主要なアーキテクチャの概念について説明します。  
  
## 参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)