---
title: リモート Web アプリケーションをデバッグするための前提条件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 197a6e9b433173f1de13e3506db79e7edf53bade
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538481"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Prerequistes for Remote Debugging Web Applications (方法 : リモート サーバーで Web アプリケーションをデバッグする)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[リモート Web アプリケーションのデバッグのための前提条件](https://docs.microsoft.com/visualstudio/debugger/prerequistes-for-remote-debugging-web-applications)します。  
  
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] デバッガーを使用すると、ローカル コンピューターやリモート サーバーで、Web アプリケーションを透過的にデバッグできます。 これは、どちらのコンピューターでもデバッガーの動作は同じであり、同じ機能を使用できることを意味します。 ただし、リモート デバッグを正常に機能させるには、いくつかの必要条件があります。  
  
-   デバッグを実行するサーバーに [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] リモート デバッグ コンポーネントをインストールする必要があります。 詳細については、次を参照してください。[リモート デバッグのセットアップ](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)します。  
  
-   既定で、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスは ASPNET ユーザー プロセスとして実行されます。 このため、それをデバッグするには、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] が実行されているコンピューターに対する管理者特権が必要です。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ワーカー プロセスの名前は、デバッグ シナリオや IIS のバージョンによって変わります。 詳細については、「 [How to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ASP.NET および AJAX アプリケーションのデバッグ](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [システム要件](../debugger/aspnet-debugging-system-requirements.md)



