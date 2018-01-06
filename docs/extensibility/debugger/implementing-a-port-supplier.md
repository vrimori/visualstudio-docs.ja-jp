---
title: "ポートのサプライヤーを実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: aa70e2a6019a97c248e6d4b411dacc222be59a1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-port-supplier"></a>ポートのサプライヤーを実装します。
ポート サプライヤーは、セッションのデバッグ マネージャー (SDM) への要求でポートを指定します。 ポートのサプライヤーは、非 DCOM マシンをデバッグするときに、または新しいデバイスをサポートする必要がある場合に実装する必要があります。 たとえば、携帯電話をデバッグするには、(おそらく IR またはセルの接続) から携帯電話に接続して、プロセスと、電話で実行されているプログラムを列挙するポートを提供するポートのサプライヤーを実装する可能性があります。  
  
 (リモート デバッグを含む)、Windows ベースのマシン上のデバッグ プログラムは、のため、このような場合に、独自のポートのサプライヤーを実装する必要はありません、Visual Studio はネイティブ モードと共通言語ランタイム (CLR) のプロセス、ポートのサプライヤーを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ポート サプライヤーの実装および登録](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM がポート サプライヤーとそのポートとやり取りする方法について説明します。  
  
 [必須のポート サプライヤー インターフェイス](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 ポート業者を取得するために実装する必要があります、インターフェイスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)