---
title: "ServerDocument クラスを使用してサーバー上のドキュメントを管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 96d69ccb51be632440474bb0aa1b32e6ebe7a68a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>ServerDocument クラスによるサーバー上のドキュメントの管理
  ServerDocument クラスを使用することができます、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]を Microsoft Office Word および Microsoft Office Excel がインストールされていない場合でも、ドキュメント レベルのカスタマイズのいくつかの側面を管理します。 実行できる管理タスクは以下のとおりです。  
  
-   ドキュメントまたはブックのデータ キャッシュにあるデータへのアクセスおよびそのデータの変更。 詳細については、次を参照してください。[キャッシュ データを操作するドキュメントで](#CachedData)です。  
  
-   ドキュメントに関連付けられているカスタマイズ アセンブリの管理。 詳細については、次を参照してください。[ドキュメントのカスタマイズを管理する](#CustomizationInfo)です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>ServerDocument クラスについて  
 ServerDocument クラスは、Office がインストールされていないコンピューターで使用するよう設計されています。 したがって、このクラスは通常、Office プロジェクトではなく、コンソール プロジェクトや Windows フォーム プロジェクトなどの Office に統合されないアプリケーションで使用します。 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll アセンブリの <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用します。  
  
 ServerDocument クラスを使用して作成されたドキュメント レベルのカスタマイズの操作に使用できます[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]です。  
  
 詳細については、Visual Studio 2010 Tools for Office Runtime およびの Office 拡張機能、.NET Framework の次を参照してください。 [Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)です。  
  
> [!NOTE]  
>  Office system 用の Visual Studio Tools で ServerDocument クラスを使用しているレガシ アプリケーションがある場合 (バージョン 3.0 ランタイム)、Visual Studio Tools for Office system (version 3.0 Runtime) アプリケーションを実行するコンピューターにインストールする必要があります。 Visual Studio 2010 Tools for Office Runtime では、そうしたアプリケーションを実行できません。  
  
##  <a name="CachedData"></a>ドキュメントでキャッシュされたデータの操作  
 ServerDocument クラスは、カスタマイズされたドキュメント内のデータ キャッシュ操作に使用できるメンバーを提供します。 キャッシュされたデータの詳細については、次を参照してください。[データをキャッシュ](../vsto/caching-data.md)と[サーバー上のドキュメントでデータにアクセスする](../vsto/accessing-data-in-documents-on-the-server.md)です。  
  
 次の表は、キャッシュされたデータの操作に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|ドキュメントにデータ キャッシュがあるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> メソッド。|  
|ドキュメント内のキャッシュされたデータにアクセスする。<br /><br /> 詳細については、「 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティ。|  
  
##  <a name="CustomizationInfo"></a>ドキュメントのカスタマイズの管理  
 ServerDocument クラスのメンバーを使用して、ドキュメントに関連付けられているカスタマイズ アセンブリを管理することができます。 たとえば、ドキュメントのカスタマイズをプログラムによって削除し、そのドキュメントをカスタマイズから除外することもできます。  
  
 次の表は、カスタマイズ アセンブリの管理に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|ドキュメントがドキュメント レベルのカスタマイズの一部であるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> メソッド。|  
|プログラムによって実行時にカスタマイズをドキュメントにアタッチする。<br /><br /> 詳細については、次を参照してください[する方法: マネージ コードの拡張をドキュメントにアタッチ。](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> メソッドの 1 つ。|  
|プログラムによって実行時にドキュメントからカスタマイズを削除する。<br /><br /> 詳細については、次を参照してください。[する方法: マネージ コードの拡張のドキュメントから削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)です。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> メソッド。|  
|ドキュメントに関連付けられている配置マニフェストの URL を取得する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> プロパティ。|  
  
## <a name="see-also"></a>参照  
 [方法: マネージ コード拡張機能をドキュメントにアタッチします。](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [方法: マネージ コード拡張をドキュメントから削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)  
  