---
title: デバッグのための言語サービスのサポート |Microsoft Docs
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
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7141c7a6b3845edda6888e1ed33abfbf8af37988
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809689"
---
# <a name="language-service-support-for-debugging"></a>デバッグのための言語サービスのサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

言語サービスが使用して、デバッガーをサポートする機能を提供できる、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>インターフェイス。 これらの機能は、ブレークポイントの検証と式のリストを指定、 **[自動変数]** ウィンドウ。  
  
 ただし、式エバリュエーターを使用する言語をデバッグする必要があります。 式エバリュエーターではデバッグ中に値を生成するために式を評価する責任を負います。 CLR 式エバリュエーターの実装方法の詳細については、参照してください。  
  
-   [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>コンパイラ出力  
 コンパイラの型は、お使いの言語のデバッグを実装するために必要事項を決定します。 コンパイラは、Windows オペレーティング システムを対象とし、デバッグ エンジンを Visual Studio に統合されているネイティブ コードとプログラムをデバッグすることができます、.pdb ファイルを書き込みます。 場合、 Microsoft intermediate language (MSIL) を生成するコンパイラ、デバッグ エンジンは、Visual Studio にも統合されているマネージ コードでプログラムをデバッグできます。 独自のオペレーティング システムまたは別のランタイム環境をコンパイラが対象とする場合は、デバッグ エンジンを記述する必要があります。  
  
 お使いの言語のデバッグの実装の詳細については、次を参照してください。 [Getting Started](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)で Visual Studio Debugging SDK。

