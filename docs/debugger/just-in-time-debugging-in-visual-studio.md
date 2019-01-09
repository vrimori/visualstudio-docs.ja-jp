---
title: 単にデバッガーを無効にする |Microsoft Docs
ms.date: 05/23/18
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f946c44039407ac413fb0b49234a8590025e12d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959788"
---
# <a name="disable-the-just-in-time-debugger"></a>Just-In-Time デバッガーを無効にする 

Just-In-Time デバッガー ダイアログ ボックスは、アプリが実行中にエラーが発生したときに開くし、アプリが継続するを防ぐ可能性があります。 

Just-In-Time デバッガーでは、エラーをデバッグする Visual Studio を起動するオプションを選択できます。 必要があります[Visual Studio](http://visualstudio.microsoft.com)または別の選択したデバッガーが、エラーに関する詳細情報を表示またはそれをデバッグしようとしています。 インストールされています。 

Visual Studio のユーザーを参照してください、エラーをデバッグしようとする必要がある場合[Just-In-Time デバッガーを使用してデバッグ](../debugger/debug-using-the-just-in-time-debugger.md)します。 場合は、エラーを修正するか、開けない Just-In-Time デバッガーを保持することはできません、 [Visual Studio からデバッグを使用しないジャスト イン タイム](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)します。 

Visual Studio のインストールが不要になった操作を行いますがあれば、可能性がある必要があります。 [Windows レジストリからデバッグを使用しないジャスト イン タイム](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)します。 

Visual Studio インストールを持っていない場合は、時間で Just スクリプトのデバッグまたはサーバー側のデバッグを無効にしてデバッグを防ぐことができます。 

- Web アプリを実行しようとしている場合は、スクリプトのデバッグを無効にします。
  
  Windows で**コントロール パネルの**  > **ネットワークとインターネット** > **インターネット オプション**、**無効にするスクリプト デバッグ (Internet Explorer)** と**スクリプトのデバッグ (その他) を無効にする**します。 正確な手順と設定は、Windows と、ブラウザーのバージョンによって異なります。
  
  ![インターネット オプションの JIT](../debugger/media/jitinternetoptions.png "JIT インターネット オプション")
  
- IIS で ASP.NET web アプリをホストしている場合は、サーバー側のデバッグを無効にします。

  1. IIS マネージャーで**機能ビュー**下で、 **ASP.NET**セクションで、ダブルクリックして **.NET コンパイル**、またはそれを選択し、 **機能を開く**で、**アクション**ウィンドウ。 
  1. **動作** > **デバッグ**、 **False**します。 手順は、古いバージョンの IIS で異なります。

時間内でデバッグを無効にした後、アプリでは、エラーを処理し、通常どおりに実行することができます。 

アプリには、まだハンドルされないエラーがある場合、エラー メッセージが表示することがあります。 またはアプリがクラッシュまたはハング可能性があります。 エラーが修正されるまで、アプリが正常に実行できません。 アプリの所有者に連絡し、その修正を依頼しようとすることができます。
