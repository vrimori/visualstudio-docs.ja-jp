---
title: "展開された ASP.NET アプリケーションのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "31"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 421c1f5f8736b9bd2cd95ac61570cc831c468c78
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-deployed-aspnet-applications"></a>展開された ASP.NET アプリケーションのデバッグ
配置されたアプリケーションを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用してデバッグするには、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスにアタッチし、デバッガーからアプリケーションのシンボルにアクセスできるようにする必要があります。 また、アプリケーションのソース ファイルを見つけて開く必要があります。 詳細については、次を参照してください。[指定シンボル (.pdb) とソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、[する方法: ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)、および[システム要件](../debugger/aspnet-debugging-system-requirements.md)です。  

> [!WARNING]
> アタッチする場合、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ワーカー プロセスのデバッグと、ブレークポイントをヒットすると、すべてのマネージ コード ワーカー プロセスが停止します。 ワーカー プロセス内のすべてのマネージ コードが停止すると、サーバーのすべてのユーザーの業務が停止する可能性があります。 運用サーバーでデバッグする場合は、事前に、実際の業務への影響について検討する必要があります。 
  
[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ワーカー プロセスにアタッチする方法は、他のリモート プロセスにアタッチする場合と同じです。 アタッチするときに正しいプロジェクトが開いていない場合、アプリケーションが中断したときに、ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、アプリケーションのソース ファイルの場所を指定するように求められます。 このダイアログ ボックスに指定するファイル名は、Web サーバー上のデバッグ シンボルで指定されているファイル名と一致する必要があります。 詳細については、次を参照してください。[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)です。 IIS でのリモート デバッグをセットアップするを参照してください。[リモート IIS コンピューター上でリモート デバッグの ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)です。
 
> [!NOTE]
>  多くの [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションは、ビジネス ロジックまたはその他の有用なコードが格納されている DLL を参照します。 このような参照は、アプリを展開するときに、DLL をローカル コンピューターから、Web アプリケーションの仮想ディレクトリの \bin フォルダーにコピーされます。 デバッグ時には、Web アプリケーションが、ローカル コンピューターの DLL ではなく、仮想ディレクトリにある DLL のコピーを参照している点に注意してください。 
  
## <a name="see-also"></a>関連項目  
 [ASP.NET アプリケーションをデバッグします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法: ASP.NET アプリケーションのデバッグを有効にします。](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [方法: ASP.NET プロセスの名前を見つける](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)