---
title: 'セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。 次の情報に関して疑わしい、または不明ながこのプロセスにアタッチされません |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dac3ad5d51e2934bd2cbdf5a8fe9ad30a4a90a8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745586"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするには危険が伴います。 以下の情報に関して疑わしい点がある場合や、不明な場合は、このプロセスにアタッチしないでください。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この警告ダイアログ ボックスは、部分的に信頼されているコードを含むプロセスや、信頼関係のないユーザーが所有するプロセスにアタッチしようとすると表示されます。 悪意のあるコードを含む信頼関係のないプロセスによって、デバッグを実行しているコンピューターに障害が発生する可能性があります。 プロセスを信頼する理由があるかどうかは、クリックして**キャンセル**デバッグを回避します。  
  
 正当なシナリオをデバッグするときに、この警告を非表示に、Visual Studio を閉じるし、このレジストリ キーの値を 1 に設定: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`、し、Visual Studio を再起動します。 シナリオのデバッグが終わったら、値を 0 にリセットし、Visual Studio を再起動します。  
  
 "信頼できるユーザー" には、ユーザー自身と、.NET Framework がインストールされているコンピューターで一般に定義される標準ユーザーのグループ (`aspnet`、`localsystem`、`networkservice`、`localservice` など) が含まれます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 名前  
 デバッグが要求されたアセンブリの名前  
  
 ユーザー  
 現在のユーザー  
  
 Attach  
 クリックすると、アタッチしてデバッグを継続します。  
  
 [アタッチしない]  
 プロセスにアタッチしません。  
  
## <a name="see-also"></a>関連項目  
 [実行中のプロセスをアタッチします。](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)



