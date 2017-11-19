---
title: "Visual Studio デバッガー拡張機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b9a14f95fbed47670b3c5b5db19e4e0e6b8ba074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio デバッガー拡張機能
Visual Studio には、プログラムでバグを追跡するための強力で使いやすいツールを提供する完全な対話型のソース コードのデバッガーが含まれています。 デバッガーでは、完全にサポート Visual Basic、c#、C と C++、および JavaScript がします。 は、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、つまりから使用可能な[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=214453)、デバッガーと同じ機能豊富な機能で他のプログラミング言語をサポートできます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ コンポーネントに、デバッグされている言語を特定するには、一般的なフロント エンド (つまり、ユーザー インターフェイス)、デバッガーです。 新しい言語では、すべての必要なをサポートして、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーはデバッグ エンジン (DE) など、必要なバック エンド コンポーネントを作成します。 ような場合は、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]で提供します。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]すべてに完全な参照を含む[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]新しい DE の作成に必要な要素です。 さらに、あるサンプルとチュートリアルを開始するために役立ちます。  
  
 デバッグのサポートと言語のプロジェクト システムのエンド ツー エンド サンプルでは、次を参照してください。、 [IronPython サンプル](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089)です。  
  
 次のセクションでは、デバッガーを使用して拡張する方法を説明する、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 対処方法について説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]は、オファーと SDK をインストールする方法をデバッグします。  
  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 に備えて、DE をデタッチする DE、プログラムから、カスタムの DE プロセスについて説明します。  
  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 式エバリュエーターを記述する必要があるかどうかについて説明します。  
  
 [デバッグ エンジンの実装方法の選択](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 DE を実装する方法について説明します。  
  
 [参照](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 ドキュメント、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API をデバッグします。  
  
 [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 共通言語ランタイムの式エバリュエーター サンプルおよびデバッグ エンジン サンプルへのリンクが含まれています。
