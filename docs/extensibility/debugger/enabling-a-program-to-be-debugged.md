---
title: デバッグするプログラムを有効化 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f8dc37e5d59738e6ef326be71e773c1e4e57351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="enabling-a-program-to-be-debugged"></a>デバッグするプログラムを有効にします。
デバッグ エンジン (DE) は、プログラムをデバッグできます、前にするには、DE を起動か、既存のプログラムにアタッチします。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ポートの取得](../../extensibility/debugger/getting-a-port.md)  
 デバッグするプログラムを有効にする最初のステップとしてポートを取得する方法について説明します。  
  
 [プログラムの登録](../../extensibility/debugger/registering-the-program.md)  
 デバッグするプログラムを有効にするのには、次の手順について説明します。 ポートに登録することです。 プログラムをデバッグできる登録されると、アタッチまたはジャスト イン タイム (JIT) デバッグのプロセスでいずれか。  
  
 [プログラムへのアタッチ](../../extensibility/debugger/attaching-to-the-program.md)  
 次の手順について説明します。 プログラムにデバッガーをアタッチします。  
  
 [起動ベースのアタッチ](../../extensibility/debugger/launch-based-attachment.md)  
 プログラムは、によって、SDM の起動時に自動的に起動ベースの添付ファイルについて説明します。  
  
 [必要なイベントの送信](../../extensibility/debugger/sending-the-required-events.md)  
 デバッグ エンジン (DE) を作成するときに、必要なイベントと手順を説明して、プログラムにアタッチします。  
  
## <a name="related-sections"></a>関連項目  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 デバッグ エンジン (DE) を定義し、DE インターフェイスと別の操作モード間の遷移にデバッガーを生じる方法で実装するサービスについて説明します。