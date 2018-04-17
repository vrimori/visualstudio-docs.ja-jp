---
title: リモート コンピューター (レガシ) からワークフローのデバッグ |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6a3058d61d2aff0369fd52e1f03726a91a2267c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>リモート コンピューターからのワークフローのデバッグ (レガシ)
このトピックをリモートのレガシをデバッグする方法について説明[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]が従来の Windows ワークフロー デザイナーで作成されたアプリケーション。 アプリケーションが [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

 インストールするときに[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]をインストールするコンポーネントのインストール オプションの 1 つは、 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]です。 これにより、リモート デバッグ コンポーネントがインストールされます。 リモート デバッグ コンポーネントは、リモート ワークフロー デバッグの対象となるコンピューター上にインストールされる必要があります。

 さらに、リモート コンピューター上のデバッグ対象である従来のワークフローのワークフロー定義を格納するアセンブリは、デバッグ元のローカル コンピューターのグローバル アセンブリ キャッシュ (GAC) にインストールされなければなりません。 たとえば、従来のワークフローがリモート コンピューター A で実行され、ローカル コンピューター B からそれをデバッグする場合には、ワークフロー定義はコンピューター B の GAC に存在する必要があります。これにより、デザイナーは、リモート コンピューター A で実行されるワークフローのワークフロー マークアップを逆シリアル化してコンピューター B に表示できます。グローバル アセンブリ キャッシュの詳細については、MSDN ライブラリを参照してください。

 [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] のリモート デバッグは、他の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] コンポーネントのリモート デバッグと同じように機能します。 詳細については、次を参照してください。 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 、MSDN ライブラリでのリモート デバッグします。

## <a name="see-also"></a>関連項目

- [従来のワークフローのデバッグ](../workflow-designer/debugging-legacy-workflows.md)