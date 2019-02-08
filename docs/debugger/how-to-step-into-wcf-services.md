---
title: '方法: WCF サービスにステップ イン |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d82ee388ff6325a92b8e82a385ace727a754ad2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017111"
---
# <a name="how-to-step-into-wcf-services"></a>方法: WCF サービスにステップインする
[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] では、WCF サービスにステップ インできます。 WCF サービスがクライアントと同じ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションにある場合、WCF サービス内のブレークポイントに到達できます。  
  
 ステップ実行を使用するには、app.config ファイルまたは Web.config ファイルでデバッグを有効にする必要があります。 デバッグを有効にして、WCF サービスにステップ インする制限については、次を参照してください。 方法については[WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)します。  
  
### <a name="to-step-into-a-wcf-service"></a>WCF サービスにステップ インするには  
  
1. WCF クライアント プロジェクトと WCF サービス プロジェクトの両方を含む [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューションを作成します。  
  
2. ソリューション エクスプローラーで、WCF クライアント プロジェクトを右クリックして、**[スタートアップ プロジェクトに設定]** をクリックします。  
  
3. app.config ファイルまたは web.config ファイルでデバッグを有効にします。 詳細については、次を参照してください。 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)します。  
  
4. クライアント プロジェクト内の、ステップ実行を開始する位置にブレークポイントを設定します。 通常、これは WCF サービス呼び出しの直前です。  
  
5. ブレークポイントまで実行した後、ステップ実行を開始します。 デバッガーがサービスに自動的にステップ インします。  
  
## <a name="see-also"></a>関連項目
 [WCF サービスのデバッグ](../debugger/debugging-wcf-services.md)   
 [WCF デバッグの制約](../debugger/limitations-on-wcf-debugging.md)   
 [方法: セルフホストされている WCF サービスをデバッグする](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
