---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
オペレーティング システムで用意されている .dll ファイルの DDEML.DLL、VERSION.DLL、WINSPOOL.DRV などが見つかりません。  このエラーが発生するのは一般的に、適切なパスにファイルがない場合、ダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) が破損しているか削除されている場合、または十分なメモリがない場合のいずれかです。  
  
### このエラーを解決するには  
  
1.  DLL が Windows のシステム パスにあることを確認します。  
  
     または  
  
     DLL を再読み込みします。  
  
     または  
  
     開いているほかのアプリケーションを閉じて、メモリを解放します。