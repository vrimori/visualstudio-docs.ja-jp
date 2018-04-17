---
title: ポートのサプライヤーを実装する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0743f307dc579f6197880b0b89acaf2db0dda08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)