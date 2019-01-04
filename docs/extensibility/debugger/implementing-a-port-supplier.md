---
title: ポート サプライヤーの実装 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: cd068f9c669b898ac3d29dadccffb6edd1e0c783
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985525"
---
# <a name="implement-a-port-supplier"></a>ポート サプライヤーを実装します。
ポート サプライヤーは、セッション デバッグ マネージャー (SDM) への要求でポートを提供します。 非 DCOM マシンまたは新しいデバイスでサポートが必要な場合にデバッグするときにポート サプライヤーを実装する必要があります。 たとえば、携帯電話へのデバッグを指定するには、ポート (IR またはセルの接続) 経由ではおそらく携帯電話に接続し、列挙のプロセスと、スマート フォンで実行されているプログラムを提供するポート サプライヤーを設定する場合があります。  
  
 (リモート デバッグも含めて)、Windows ベースのコンピューターでプログラムのデバッグのため、このような場合、独自のポート サプライヤーを設定する必要はありません、Visual Studio はネイティブ モードと共通言語ランタイム (CLR) のプロセス、ポート サプライヤーを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [実装し、ポートのサプライヤーの登録](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 ポート サプライヤーとそのポートで、SDM をやり取りする方法について説明します。  
  
 [必要なポート サプライヤー インターフェイス](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 ポート サプライヤーを取得するために実装する必要がありますインターフェイスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)