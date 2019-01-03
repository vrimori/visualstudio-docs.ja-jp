---
title: デバッグ エンジンの実装方法の選択 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97b3c82a59736b72a58237f1e53ff39e9e3b86b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818353"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>デバッグ エンジンの実装方法を選択します。
デバッグ エンジン (DE) の実装戦略を決定するのにには、実行時のアーキテクチャを使用します。 デバッグ エンジンでのプロセスをデバッグするプログラムを作成できます。 プロセスを作成、デバッグ エンジンでの Visual Studio セッション デバッグ マネージャー (SDM)。 または、デバッグ エンジンのプロセス外にこれらの両方を作成します。 次のガイドラインではこれら 3 つの戦略の中から選択できます。  
  
## <a name="guidelines"></a>ガイドライン  
 アウト プロセスに DE のことはできますが、SDM とをデバッグするプログラムの両方には通常そう理由。 プロセスの境界を越えて呼び出しは比較的低速です。  
  
 デバッグ エンジンは Win32 ネイティブ ランタイム環境と、共通言語ランタイム環境に既に提供されます。 環境のどちらの DE を置換するした場合、SDM をインプロセス DE を作成する必要があります。  
  
 それ以外の場合、作成するか、SDM をインプロセス DE またはデバッグして同じプロセスをプログラムにします。 デの式エバリュエーターが、プログラムのシンボル ストアに頻繁にアクセスを必要とかどうかを考慮する必要があります。 または、シンボル ストアを高速アクセス用のメモリに読み込むことができる場合。 また、次の方法を検討してください。  
  
-   式エバリュエーターと、シンボル ストアの間の多数の呼び出しが存在しない場合、またはシンボル ストアは、SDM のメモリ領域に読み取ることができる場合、SDM をインプロセス DE を作成します。 プログラムにアタッチするときに、SDM デバッグ エンジンの CLSID を返す必要があります。 SDM は、この CLSID を使用して、DE のインプロセス インスタンスを作成します。  
  
-   場合は、DE シンボル ストアにアクセスするプログラムを呼び出す必要があります、DE、インプロセスをプログラムで作成します。 この場合、プログラムは、DE のインスタンスを作成します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)