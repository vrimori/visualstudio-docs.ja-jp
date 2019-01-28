---
title: デバッガーの拡張性の概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 902551df1ff58e6d970b760e684df9861aac6fb4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043181"
---
# <a name="get-started-with-debugger-extensibility"></a>デバッガーの拡張性を概要します。
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]の作成し、カスタマイズのデバッガーのコンポーネント内からプログラムをデバッグするために使用する必要のある情報を提供します、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッグと広範な使いやすさの前に行われるテストから派生した機能強化が追加[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガー。 使用することができます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をステップ実行するか、多言語アプリケーションでは、デバッグ、稼働中のアプリケーションと多言語ソリューションのデバッグ中に変数の編集を実装できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] デバッグして、実行されたプロセス外の - デバッグ中のプログラムでは、さほど、アプリケーションのプロセス空間では、そのため。 その結果、デバッグ、プログラムの影響を与えずに、デバッガーで対話するコンポーネントを記述しやすくなります。  
  
 最適に使用する、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、次のものでは、理解しておく必要があります。  
  
- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE)  
  
- C++ プログラミング言語  
  
- ATL COM  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッガーを拡張するためのロードマップ](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 コンパイラとその出力によって、製品でのデバッグの実装プロセスについて説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 概要、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ エンジン (DE)、式エバリュエーター (EE) およびシンボル ハンドラー (SH) のコンポーネントをデバッグします。  
  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デバッグ エンジン (DE) が同時にして動作し、コード、ドキュメント、および式の評価のコンテキスト内で方法について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。