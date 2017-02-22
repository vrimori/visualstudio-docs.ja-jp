---
title: "Visual Studio デバッガーの拡張性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ [Visual Studio]、[SDK のデバッグ"
  - "SDK のデバッグ"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio デバッガーの拡張性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio には、プログラムでバグを追跡するための強力で使いやすいツールを提供する完全な対話型のソース コードのデバッガーが含まれています。 デバッガーは、完全なサポート Visual Basic、c\#、C と C\+\+ および JavaScript です。 ただし、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], 、つまりから利用可能な [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=214453),, 、および他のプログラミング言語は、同じ豊富な機能を使用してデバッガーでサポートされることができます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッガーでは、一般的なフロント エンド \(つまり、ユーザー インターフェイス\) は、さらに、デバッグ中の言語に固有のデバッグのコンポーネントにします。 サポートに必要なすべての新しい言語、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッガーはデバッグ エンジン \(DE\) など、必要なバックエンド コンポーネントを作成します。 ここで、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] を受信します。  
  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] すべてに完全なリファレンスが含まれています [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 新しい DE の作成に必要な要素です。 さらに、あるサンプルおよび開始するために役立つチュートリアルです。  
  
 デバッグのサポートと言語のプロジェクト システムのエンド ツー エンド サンプルでは、次を参照してください。、 [IronPython sample](http://msdn.microsoft.com/ja-jp/4c41695c-12c1-4670-b43b-d8d84c9e4089)です。  
  
 次のセクションでは、使用して、デバッガーを拡張する方法を説明する、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
## このセクションの内容  
 [作業の開始](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 対処方法について説明 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は、オファーと SDK をインストールする方法をデバッグします。  
  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 プログラムを DE をデタッチする DE の準備から、カスタムの DE プロセスについて説明します。  
  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 式エバリュエーターを記述する必要があるかどうかについて説明します。  
  
 [デバッグ エンジンの実装方法を選択します。](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 DE を実装する方法について説明します。  
  
 [参照](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 ドキュメント、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API をデバッグします。  
  
 [サンプル](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 共通言語ランタイムの式エバリュエーター サンプルとデバッグ エンジン サンプルへのリンクが含まれています。