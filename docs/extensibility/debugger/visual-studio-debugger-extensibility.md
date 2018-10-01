---
title: Visual Studio デバッガーの拡張性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0be4a96854315bcf8b83db86692758e198980cd
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370927"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio デバッガーの拡張性
Visual Studio には、プログラムでバグを追跡するための強力で使いやすいツールを提供する完全な対話型のソース コードのデバッガーが含まれています。 デバッガーでは、完全なサポート Visual Basic、c#、C と C++ および JavaScript が。 ただし、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、つまりから使用可能な[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=214453)、他のプログラミング言語は同じ豊富な機能を使用してデバッガーでサポートされます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーは、一般的なフロント エンド (つまり、ユーザー インターフェイス)、デバッグ コンポーネントは、さらに、デバッグ中の言語に固有です。 によってサポートのために必要なすべての新しい言語は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーはデバッグ エンジン (DE) など、必要なバックエンド コンポーネントを作成します。 このポイントは、where、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]が用意されています。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]すべてに完全なリファレンスが含まれています[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]新しい DE の作成に必要な要素です。 さらに、あるサンプルとチュートリアルの作業を開始するのに役立つ。  
  
 デバッグのサポートと言語のプロジェクト システムの完全なサンプルを参照してください、 [IronPython サンプル](https://www.microsoft.com/download/details.aspx?id=55984)します。  
  
 次のセクションを使用して、デバッガーを拡張する方法を説明します、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [開始するには](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 点について説明します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プランと、SDK をインストールする方法をデバッグします。  
  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 ドイツ、DE をデタッチするため、プログラムの準備から、カスタム DE プロセスについて説明します。  
  
 [CLR の式エバリュエーターを書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 式エバリュエーターを記述する必要があるかどうかについて説明します。  
  
 [デバッグ エンジンの実装方法を選択します。](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 DE を実装する方法について説明します。  
  
 [参照](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 ドキュメント、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API をデバッグします。  
  
 [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 共通言語ランタイム式エバリュエーター サンプルとデバッグ エンジンのサンプルへのリンクが含まれています。
