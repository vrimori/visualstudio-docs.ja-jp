---
title: "リモート コンピューター (レガシ) からワークフローのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: b4b9207702e6b4c3b93838eccfe1da15c42b5baa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>リモート コンピューターからのワークフローのデバッグ (レガシ)
このトピックでは、従来の [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]を使用して作成された、リモートにある従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] アプリケーションをデバッグする方法について説明します。 アプリケーションが [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。  
  
 インストールするときに[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]をインストールするコンポーネントのインストール オプションの 1 つは、 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]です。 これにより、リモート デバッグ コンポーネントがインストールされます。 リモート デバッグ コンポーネントは、リモート ワークフロー デバッグの対象となるコンピューター上にインストールされる必要があります。  
  
 さらに、リモート コンピューター上のデバッグ対象である従来のワークフローのワークフロー定義を格納するアセンブリは、デバッグ元のローカル コンピューターのグローバル アセンブリ キャッシュ (GAC) にインストールされなければなりません。 たとえば、従来のワークフローがリモート コンピューター A で実行され、ローカル コンピューター B からそれをデバッグする場合には、ワークフロー定義はコンピューター B の GAC に存在する必要があります。これにより、デザイナーは、リモート コンピューター A で実行されるワークフローのワークフロー マークアップを逆シリアル化してコンピューター B に表示できます。グローバル アセンブリ キャッシュの詳細については、MSDN ライブラリを参照してください。  
  
 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] のリモート デバッグは、他の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コンポーネントのリモート デバッグと同じように機能します。 詳細については、次を参照してください。 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 、MSDN ライブラリでのリモート デバッグします。  
  
## <a name="see-also"></a>参照  
 [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)