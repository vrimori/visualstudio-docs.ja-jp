---
title: '方法: WCF サービスにステップ イン |Microsoft Docs'
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
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b779c8bc2e6da3975f1f70265482c706c9141375
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539302"
---
# <a name="how-to-step-into-wcf-services"></a>方法 : WCF サービスにステップ インする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: WCF サービスにステップ イン](https://docs.microsoft.com/visualstudio/debugger/how-to-step-into-wcf-services)します。  
  
[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] では、WCF サービスにステップ インできます。 WCF サービスがクライアントと同じ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ソリューションにある場合、WCF サービス内のブレークポイントに到達できます。  
  
 ステップ実行を使用するには、app.config ファイルまたは Web.config ファイルでデバッグを有効にする必要があります。 デバッグを有効にして、WCF サービスにステップ インする制限については、次を参照してください。 方法については[WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)します。  
  
### <a name="to-step-into-a-wcf-service"></a>WCF サービスにステップ インするには  
  
1.  WCF クライアント プロジェクトと WCF サービス プロジェクトの両方を含む [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ソリューションを作成します。  
  
2.  ソリューション エクスプローラで、WCF クライアント プロジェクトを右クリックし をクリックし、**スタートアップ プロジェクトとして設定**します。  
  
3.  app.config ファイルまたは web.config ファイルでデバッグを有効にします。 詳細については、次を参照してください。 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)します。  
  
4.  クライアント プロジェクト内の、ステップ実行を開始する位置にブレークポイントを設定します。 通常、これは WCF サービス呼び出しの直前です。  
  
5.  ブレークポイントまで実行した後、ステップ実行を開始します。 デバッガーがサービスに自動的にステップ インします。  
  
## <a name="see-also"></a>関連項目  
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)   
 [方法 : セルフホストされている WCF サービスをデバッグする](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



