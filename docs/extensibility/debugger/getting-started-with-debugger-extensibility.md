---
title: "デバッガーの機能拡張の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 258fcfcc97d0a6b1455ec60201527cde3e87f9b8
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-debugger-extensibility"></a>デバッガーの機能拡張を入門
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]を作成および内からプログラムをデバッグするためのデバッガー コンポーネントのカスタマイズに必要な情報を提供、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグと広範な利便性が以前に行われるテストから派生した機能強化が追加[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッガーです。 使用する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をステップ実行するか、多言語アプリケーションのデバッグ、稼働中のアプリケーションと多言語ソリューションのデバッグ中に変数の編集を実装できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグして、実行のプロセス外でデバッグするプログラムは、アプリケーションのプロセス空間で目立たないためです。 その結果、デバッグ、プログラムの影響を与えずに、デバッガーと対話するコンポーネントを作成する簡単です。  
  
 最大限に活用する、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]、以下について理解する必要があります。  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE)  
  
-   C++ プログラミング言語  
  
-   ATL COM  
  
## <a name="in-this-section"></a>このセクションの内容  
 [デバッガーを拡張するためのロードマップ](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 コンパイラとその出力によって、製品でのデバッグを実装する手順について説明します。  
  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)  
 概要、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ エンジン (DE)、式エバリュエーター (EE) シンボル ハンドラー (SH) などのコンポーネントをデバッグします。  
  
 [デバッガーの概念](../../extensibility/debugger/debugger-concepts.md)  
 デバッグ アーキテクチャ、主要な概念をについて説明します。  
  
 [デバッガー コンテキスト](../../extensibility/debugger/debugger-contexts.md)  
 コード、ドキュメント、および式の評価のコンテキスト内でデバッグ エンジン (DE) がどのように同時に動作について説明します。 3 つのコンテキスト、場所、位置、またはそれに関連する評価ごとに説明します。  
  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)  
 プログラムを起動して、式の評価などのさまざまなデバッグ タスクへのリンクが含まれています。
