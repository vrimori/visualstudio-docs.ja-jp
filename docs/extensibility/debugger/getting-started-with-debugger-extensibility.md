---
title: デバッガーの機能拡張の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98d6e0200c1a68ae3819d3276ce8a04aaada2e78
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102695"
---
# <a name="getting-started-with-debugger-extensibility"></a>デバッガーの機能拡張の概要
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]を作成し、内からプログラムをデバッグするために使用するデバッガー コンポーネントをカスタマイズするために必要な情報を提供、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッグと、基に広範な使いやすさの前に行われるテストの機能強化が追加[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーです。 使用することができます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をステップ実行するか、多言語アプリケーションでは、デバッグ、稼働中のアプリケーションと多言語ソリューションをデバッグ中に変数の編集を実装できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッグして、実行のプロセスのデバッグ中のプログラムでは、アプリケーションのプロセス空間で煩雑であるため。 その結果、デバッグ、プログラムの影響を与えずに、デバッガーでは、対話するコンポーネントを記述を簡単になります。  
  
 最大限に活用する、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]次に慣れておく必要があります。  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE)  
  
-   C++ のプログラミング言語  
  
-   ATL COM  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッガーを拡張するためのロードマップ](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 実装によっては、コンパイラとその出力、製品にデバッグ プロセスの概要を示します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 概要を示します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ エンジン (DE)、式エバリュエーター (EE) シンボル ハンドラー (SH) などのコンポーネントをデバッグします。  
  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デバッグ エンジン (DE) の動作方法に同時にコード、ドキュメント、および式の評価のコンテキスト内でについて説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式を評価するなど、さまざまなデバッグ タスクへのリンクが含まれています。