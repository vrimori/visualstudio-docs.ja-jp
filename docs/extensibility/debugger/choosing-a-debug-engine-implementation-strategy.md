---
title: "デバッグ エンジン実装ストラテジの選択 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d08d82f867ac2723ff68da615d5dc6977b8038af
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>デバッグ エンジン実装方法を選択します。
デバッグ エンジン (DE) の実装方法を決定するのにには、実行時のアーキテクチャを使用します。 デバッグ エンジンは、同じプロセスをデバッグしようとするプログラムを Visual Studio セッション デバッグ マネージャー (SDM)、またはそれらの両方にアウトはプロセスのプロセスで作成可能性があります。 次のガイドラインはこれら 3 つの戦略の中から選択する際に役立ちます。  
  
## <a name="guidelines"></a>ガイドライン  
 アウト プロセスである DE のことができますが、SDM との両方に、プログラム デバッグできるように、通常はありませんの理由。 プロセスの境界を越えての呼び出しは、比較的低速です。  
  
 デバッグ エンジンは、Win32 のネイティブ ランタイム環境と、共通言語ランタイム環境に既に提供されています。 デは、これらの環境のいずれかに置き換える必要があります、SDM のインプロセス DE を作成する必要があります。  
  
 それ以外の場合、間、SDM をインプロセスまたは同じプロセスをデバッグするプログラム、DE を作成することができます。 ことが重要、DE の式エバリュエーターが、プログラムのシンボル ストアに頻繁にアクセスを必要があるかどうかと、シンボル ストアを迅速なアクセス用のメモリに読み込まれるかどうかを検討してください。 また、次の点を検討してください。  
  
-   式エバリュエーターと、シンボル ストア間で多数の呼び出しが存在しない場合、または SDM メモリ領域に、シンボル ストアを読み取ることができる場合は、SDM にインプロセス DE を作成します。 プログラムにアタッチするときに、SDM デバッグ エンジンの CLSID を返す必要があります。 SDM では、この CLSID を使用して、DE のインプロセスでインスタンスを作成します。  
  
-   デには、シンボル ストアにアクセスするプログラムを呼び出す必要があります、プログラムでインプロセス DE を作成します。 この場合、プログラムは、DE のインスタンスを作成します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)