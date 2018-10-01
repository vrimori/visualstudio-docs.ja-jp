---
title: 'エラー: サーバーに自動的にステップ インできません |。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d75ed4ddb42705b95a5ddd834596bc828e0f3ec2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533993"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>エラー : サーバーに自動的にステップ インできません。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[エラー: ステップに、サーバーを自動的にできません。](https://docs.microsoft.com/visualstudio/debugger/error-unable-to-automatically-step-into-the-server)します。  
  
このエラーは次のように表示されます。  
  
 サーバーに自動的にステップ インできません。 デバッガーは、リモート プロシージャが実行される前に通知されませんでした。  
  
 このエラーは、Web サービスにステップ インしようとすると発生することがあります (「 [XML Web サービスへのステップ イン](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)」を参照してください)。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] が正しくセットアップされていない場合に発生する可能性があります。  
  
 考えられる原因:  
  
-   Web.config ファイル、[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]アプリケーション デバッグを"true"を設定しません (を参照してください[ASP.NET アプリケーションのデバッグ モード](../debugger/how-to-enable-debugging-for-aspnet-applications.md))。  
  
-   バージョンの[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Visual Studio をインストールした後にインストールされました。 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Visual Studio の前にインストールする必要があります。 この問題を解決するには、Windows の **[コントロール パネル]** で **[プログラムと機能]** を使用して、Visual Studio のインストールを修復します。  
  
## <a name="see-also"></a>関連項目  
 [リモート デバッグ エラーとトラブルシューティング](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



