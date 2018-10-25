---
title: デバッガーの拡張性の概要 |Microsoft Docs
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
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 321c4790decb81d91ef57afe6bedffcd89a179e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304974"
---
# <a name="getting-started-with-debugger-extensibility"></a>デバッガーの機能拡張の開始
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]を作成およびカスタマイズ内からプログラムをデバッグするために使用するデバッガー コンポーネントに必要な情報を提供します、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] デバッグと広範な使いやすさの前に行われるテストから派生した機能強化が追加[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッガー。 使用することができます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]をステップ実行するか、多言語アプリケーションでは、デバッグ、稼働中のアプリケーションと多言語ソリューションのデバッグ中に変数の編集を実装できます。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] デバッグして、実行されたプロセス外の - デバッグ中のプログラムでは、さほど、アプリケーションのプロセス空間では、そのため。 その結果、デバッグ、プログラムの影響を与えずに、デバッガーで対話するコンポーネントを記述しやすくなります。  
  
 最適に使用する、 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]、次について理解する必要があります。  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境 (IDE)  
  
-   C++ プログラミング言語  
  
-   ATL COM  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッガーを拡張するためのロードマップ](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 コンパイラとその出力によって、製品でのデバッグの実装プロセスについて説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 概要、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッグ エンジン (DE)、式エバリュエーター (EE) およびシンボル ハンドラー (SH) のコンポーネントをデバッグします。  
  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャの主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 デバッグ エンジン (DE) が同時にして動作し、コード、ドキュメント、および式の評価のコンテキスト内で方法について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。

