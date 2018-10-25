---
title: リモート Web アプリケーションをデバッグするための前提条件 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 448e6e7705e4df7330abce0e919adc705721102c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227306"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Prerequistes for Remote Debugging Web Applications (方法 : リモート サーバーで Web アプリケーションをデバッグする)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デバッガーを使用すると、ローカル コンピューターやリモート サーバーで、Web アプリケーションを透過的にデバッグできます。 これは、どちらのコンピューターでもデバッガーの動作は同じであり、同じ機能を使用できることを意味します。 ただし、リモート デバッグを正常に機能させるには、いくつかの必要条件があります。  
  
-   デバッグを実行するサーバーに [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] リモート デバッグ コンポーネントをインストールする必要があります。 詳細については、次を参照してください。[リモート デバッグのセットアップ](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)します。  
  
-   既定で、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスは ASPNET ユーザー プロセスとして実行されます。 このため、それをデバッグするには、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] が実行されているコンピューターに対する管理者特権が必要です。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって変わります。 詳細については、「 [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET および AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)



