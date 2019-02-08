---
title: デプロイされた ASP.NET アプリケーションのデバッグ |Microsoft Docs
ms.date: 06/30/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: aeb64c445acc0881ce808f9261c42f5205c4d979
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009519"
---
# <a name="debugging-deployed-aspnet-applications"></a>デプロイされた ASP.NET アプリケーションのデバッグ
配置されたアプリケーションを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用してデバッグするには、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスにアタッチし、デバッガーからアプリケーションのシンボルにアクセスできるようにする必要があります。 また、アプリケーションのソース ファイルを見つけて開く必要があります。 詳細については、次を参照してください。[指定シンボル (.pdb) とソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、[方法。ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)、および[システム要件](../debugger/aspnet-debugging-system-requirements.md)します。  

> [!WARNING]
> アタッチする場合、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ワーカー プロセスのデバッグとブレークポイントのヒットは、すべてのマネージ コードでは、ワーカー プロセスが停止します。 ワーカー プロセス内のすべてのマネージド コードが停止すると、サーバーのすべてのユーザーの業務が停止する可能性があります。 運用サーバーでデバッグする場合は、事前に、実際の業務への影響について検討する必要があります。 
  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスにアタッチする方法は、他のリモート プロセスにアタッチする場合と同じです。 アタッチしたときに正しいプロジェクトが開いていない場合、アプリケーションが中断するとダイアログ ボックスが表示されます。 このダイアログ ボックスでは、アプリケーションのソース ファイルの場所を指定するように求められます。 このダイアログ ボックスに指定するファイル名は、Web サーバー上のデバッグ シンボルで指定されているファイル名と一致する必要があります。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。 IIS でのリモート デバッグを設定するを参照してください。 [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)します。
 
> [!NOTE]
>  多くの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションは、ビジネス ロジックまたはその他の有用なコードが格納されている DLL を参照します。 このような参照は、アプリを展開するときに、DLL をローカル コンピューターから、Web アプリケーションの仮想ディレクトリの \bin フォルダーにコピーします。 デバッグ時には、Web アプリケーションが、ローカル コンピューターの DLL ではなく、仮想ディレクトリにある DLL のコピーを参照している点に注意してください。 
  
## <a name="see-also"></a>関連項目
 [ASP.NET アプリケーションをデバッグする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法: ASP.NET アプリケーションのデバッグを有効にする](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法: ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
