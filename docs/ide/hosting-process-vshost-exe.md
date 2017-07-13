---
title: "ホスト プロセス (vshost.exe) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 96cd56eaeea20b2b0defcb60a188c9e13c19ec6a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# ホスト プロセス (vshost.exe)
<a id="hosting-process-vshostexe" class="xliff"></a>
Visual Studio のホスト プロセスは、デバッグのパフォーマンスを向上させ、部分信頼のデバッグを可能にし、デザイン時に式を評価できるようにする機能です。 ホスト プロセスのファイルは、ファイル名に vshost が含まれ、プロジェクトの出力フォルダーに配置されます。 詳しくは、「[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)」をご覧ください。  
  
> [!NOTE]
>  ホスト プロセスのファイル (. vshost.exe) は、Visual Studio によって使われるものなので、直接実行したり、アプリケーションと共に配置したりしないでください。  
  
## デバッグ パフォーマンスの向上
<a id="improved-debugging-performance" class="xliff"></a>  
 ホスト プロセスは、アプリケーション ドメインを作成し、デバッガーをアプリケーションに関連付けます。 これらのタスクを実行すると、デバッグが開始されてからアプリケーションが実行を始めるまでに、大きな遅延が発生する可能性があります。 ホスト プロセスは、アプリケーション ドメインの作成とデバッガーの関連付けをバックグラウンドで行い、アプリケーションの実行と実行の間でアプリケーション ドメインとデバッガーの状態を保存することにより、パフォーマンスを向上させます。 アプリケーション ドメインについて詳しくは、「[アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)」をご覧ください。  
  
## 部分信頼のデバッグ
<a id="partial-trust-debugging" class="xliff"></a>  
 **プロジェクト デザイナー**の [[セキュリティ] ページ](../ide/reference/security-page-project-designer.md)では、アプリケーションを部分信頼アプリケーションとして指定することができます。 部分信頼アプリケーションをデバッグするには、アプリケーション ドメインの特別な初期化が必要です。 ホスト プロセスは、この初期化を処理します。  
  
## デザイン時の式評価
<a id="design-time-expression-evaluation" class="xliff"></a>  
 デザイン時の式評価を使うと、**[イミディエイト]** ウィンドウからコードをテストすることができ、アプリケーションを実行する必要がありません。 ホスト プロセスは、デザイン時の式評価の間にこのコードを実行します。 詳しくは、「[イミディエイト ウィンドウ](../ide/reference/immediate-window.md)」をご覧ください。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)   
 [方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)   
 [イミディエイト ウィンドウ](../ide/reference/immediate-window.md)   
 [アプリケーション ドメイン](/dotnet/framework/app-domains/application-domains)
