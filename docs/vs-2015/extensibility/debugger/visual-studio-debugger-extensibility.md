---
title: Visual Studio デバッガーの拡張性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b5e9e7a3db38b5138f6392ff89f3a3bb4a13303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743491"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio デバッガーの拡張性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio には、プログラムでバグを追跡するための強力で使いやすいツールを提供する完全な対話型のソース コードのデバッガーが含まれています。 デバッガーでは、完全なサポート Visual Basic、c#、C と C++ および JavaScript が。 ただし、 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]、つまりから使用可能な[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=214453)、および他のプログラミング言語は同じ豊富な機能を使用してデバッガーでサポートされます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッガーは、一般的なフロント エンド (つまり、ユーザー インターフェイス)、デバッグ コンポーネントは、さらに、デバッグ中の言語に固有です。 によってサポートのために必要なすべての新しい言語は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッガーはデバッグ エンジン (DE) など、必要なバックエンド コンポーネントを作成します。 ような場合は、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]が用意されています。  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]すべてに完全なリファレンスが含まれています[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]新しい DE の作成に必要な要素です。 さらに、あるサンプルとチュートリアルの作業を開始するのに役立つ。  
  
 デバッグのサポートと言語のプロジェクト システムのエンド ツー エンド サンプルでは、次を参照してください。、 [IronPython サンプル](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089)します。  
  
 次のセクションを使用して、デバッガーを拡張する方法を説明します、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [はじめに](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 点について説明します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プランと、SDK をインストールする方法をデバッグします。  
  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 ドイツ、DE をデタッチするため、プログラムの準備から、カスタム DE プロセスについて説明します。  
  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 式エバリュエーターを記述する必要があるかどうかについて説明します。  
  
 [デバッグ エンジンの実装方法の選択](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 DE を実装する方法について説明します。  
  
 [参照](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 ドキュメント、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API をデバッグします。  
  
 [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 共通言語ランタイム式エバリュエーター サンプルとデバッグ エンジンのサンプルへのリンクが含まれています。

