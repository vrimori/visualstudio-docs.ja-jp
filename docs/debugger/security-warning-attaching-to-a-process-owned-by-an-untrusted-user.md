---
title: 'セキュリティの警告: 信頼されていないユーザーが所有するプロセスにアタッチするは危険です。 次の情報に関して疑わしい点またはことを確認して場合がこのプロセスにアタッチされません |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>セキュリティの警告: 信頼されていないユーザーが所有するプロセスにアタッチするは危険です。 次の情報に関して疑わしい点またはことを確認して場合がこのプロセスにアタッチできません。
この警告ダイアログ ボックスは、部分的に信頼されているコードを含むプロセスや、信頼関係のないユーザーが所有するプロセスにアタッチしようとすると表示されます。 悪意のあるコードを含む信頼関係のないプロセスによって、デバッグを実行しているコンピューターに障害が発生する可能性があります。 プロセスを信頼する理由がないかどうかをクリックする必要があります**キャンセル**デバッグを回避します。  
  
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