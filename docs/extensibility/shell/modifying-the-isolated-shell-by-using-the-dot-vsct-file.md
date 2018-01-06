---
title: "使用して分離シェルを変更します。Vsct ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 631aaaf4bf3d36cf5b83c8e67791c453cdfed925
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>使用して分離シェルを変更します。Vsct ファイル
Visual Studio 分離シェル プロジェクト用の UI プロジェクトには、どのアプリケーション グループと個々 のコマンドは、アプリケーションで使用可能なを指定できる .vsct ファイルが含まれています。 次に、変更されていない .vsct ファイルからの抜粋を示します。  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 既定では、ほとんどのコマンドおよびコマンド グループが含まれます。 コマンドまたはコマンド グループを除外する、単にコメントを解除するコマンドまたはグループ。  
  
 たとえば、削除するには、次のペインと前のペインのコマンドのコメントを解除、`No_PaneNextPaneCommand`と`No_PanePrevPaneCommand`エントリ。  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 詳細な例はこれらのカスタマイズを参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
## <a name="referenced-files"></a>参照先のファイル  
 アプリケーションの既定の .vsct ファイルでは、次のファイルを参照します。 これらのファイルは、\VisualStudioIntegration\Common\Inc\、Visual Studio SDK インストール ディレクトリのサブディレクトリにあります。  
  
|ファイル|説明|  
|----------|-----------------|  
|wbids.h|Web 参照パッケージの UI の id。|  
|AppIDCmdUsed.vsct|プライマリの Visual Studio の UI 要素のコマンド テーブルです。|  
|EmulatorCmdUsed.vsct|Emacs と概要エディター エミュレーションの UI 要素のコマンド テーブルです。|  
|Vsdebugguids.h|コマンドのオプション ページで、Visual Studio デバッガーの他の機能の Guid を定義します。|  
|VsDbgCmdUsed.vsct|デバッガーのコマンド テーブルです。|  
  
 AppIDCmdUsed.vsct ファイルには、アプリケーションの .vsct ファイルで定義されたシンボルに基づく Visual Studio の UI 要素が含まれています。  
  
 詳細については、次を参照してください。 [XML コマンド テーブルのデザイン (です。Vsct) ファイル](../internals/designing-xml-command-table-dot-vsct-files.md)と[VSCT XML スキーマ リファレンス](../vsct-xml-schema-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [Visual Studio の分離シェル](visual-studio-isolated-shell.md)