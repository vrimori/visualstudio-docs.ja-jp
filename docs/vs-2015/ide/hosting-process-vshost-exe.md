---
title: ホスト プロセス (vshost.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d45da37dae805399f9af8591bcd017ed61a975c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216708"
---
# <a name="hosting-process-vshostexe"></a>ホスト プロセス (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio のホスト プロセスは、デバッグのパフォーマンスを向上させ、部分信頼のデバッグを可能にし、デザイン時に式を評価できるようにする機能です。 ホスト プロセスのファイルは、ファイル名に vshost が含まれ、プロジェクトの出力フォルダーに配置されます。 詳しくは、「[プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)」をご覧ください。  
  
> [!NOTE]
>  ホスト プロセスのファイル (. vshost.exe) は、Visual Studio によって使われるものなので、直接実行したり、アプリケーションと共に配置したりしないでください。  
  
## <a name="improved-debugging-performance"></a>デバッグ パフォーマンスの向上  
 ホスト プロセスは、アプリケーション ドメインを作成し、デバッガーをアプリケーションに関連付けます。 これらのタスクを実行すると、デバッグが開始されてからアプリケーションが実行を始めるまでに、大きな遅延が発生する可能性があります。 ホスト プロセスは、アプリケーション ドメインの作成とデバッガーの関連付けをバックグラウンドで行い、アプリケーションの実行と実行の間でアプリケーション ドメインとデバッガーの状態を保存することにより、パフォーマンスを向上させます。 アプリケーション ドメインについて詳しくは、「[アプリケーション ドメイン](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)」をご覧ください。  
  
## <a name="partial-trust-debugging"></a>部分信頼のデバッグ  
 **プロジェクト デザイナー**の [[セキュリティ] ページ](../ide/reference/security-page-project-designer.md)では、アプリケーションを部分信頼アプリケーションとして指定することができます。 部分信頼アプリケーションをデバッグするには、アプリケーション ドメインの特別な初期化が必要です。 ホスト プロセスは、この初期化を処理します。  
  
## <a name="design-time-expression-evaluation"></a>デザイン時の式評価  
 デザイン時の式評価を使うと、**[イミディエイト]** ウィンドウからコードをテストすることができ、アプリケーションを実行する必要がありません。 ホスト プロセスは、デザイン時の式評価の間にこのコードを実行します。 詳しくは、「[イミディエイト ウィンドウ](../ide/reference/immediate-window.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [プロセスのデバッグとホスト](../debugger/debugging-and-the-hosting-process.md)   
 [方法 : ホスト プロセスを無効にする](../ide/how-to-disable-the-hosting-process.md)   
 [イミディエイト ウィンドウ](../ide/reference/immediate-window.md)   
 [アプリケーション ドメイン](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)



