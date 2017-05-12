---
title: "ServerDocument クラスによるサーバー上のドキュメントの管理"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発], 管理 (サーバーでの)"
  - "Office ドキュメント [Visual Studio での Office 開発, 管理 (サーバーでの)"
  - "ServerDocument クラス, 管理 (サーバーのドキュメントを)"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# ServerDocument クラスによるサーバー上のドキュメントの管理
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の ServerDocument クラスを使用すると、Microsoft Office Word と Microsoft Office Excel がインストールされていない場合でも、ドキュメント レベルのカスタマイズに対してさまざまな管理タスクを行うことができます。  実行できる管理タスクは以下のとおりです。  
  
-   ドキュメントまたはブックのデータ キャッシュにあるデータへのアクセスおよびそのデータの変更。  詳細については、「[ドキュメントのキャッシュされたデータの操作](#CachedData)」を参照してください。  
  
-   ドキュメントに関連付けられているカスタマイズ アセンブリの管理。  詳細については、「[ドキュメントのカスタマイズの管理](#CustomizationInfo)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## ServerDocument クラスについて  
 ServerDocument クラスは Office がインストールされていないコンピューターでの使用を目的としています。  したがって、このクラスは通常、Office プロジェクトではなく、コンソール プロジェクトや Windows フォーム プロジェクトなどの Office に統合されないアプリケーションで使用します。  Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll アセンブリの <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用します。  
  
 ServerDocument クラスは、[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成されたドキュメント レベルのカスタマイズの操作に使用できます。  
  
 Visual Studio 2010 Tools for Office Runtime と .NET Framework 用の Office 拡張機能の詳細については、「[Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)」を参照してください。  
  
> [!NOTE]  
>  レガシ アプリケーションで Visual Studio Tools for Office System \(Version 3.0 Runtime\) の ServerDocument クラスを使用する場合は、そのアプリケーションを実行するコンピューターに Visual Studio Tools for Office System \(Version 3.0 Runtime\) がインストールされている必要があります。  Visual Studio 2010 Tools for Office Runtime では、そうしたアプリケーションを実行できません。  
  
##  <a name="CachedData"></a> ドキュメントのキャッシュされたデータの操作  
 ServerDocument クラスには、カスタマイズされたドキュメント内のデータ キャッシュの操作に使用できるメンバーが用意されています。  キャッシュされたデータの詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」および「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。  
  
 次の表は、キャッシュされたデータの操作に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|---------|--------------|  
|ドキュメントにデータ キャッシュがあるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> メソッド。|  
|ドキュメント内のキャッシュされたデータにアクセスする。<br /><br /> 詳細については、「[サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)」を参照してください。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティ。|  
  
##  <a name="CustomizationInfo"></a> ドキュメントのカスタマイズの管理  
 ServerDocument クラスのメンバーを使用して、ドキュメントに関連付けられているカスタマイズ アセンブリを管理できます。  たとえば、ドキュメントのカスタマイズをプログラムによって削除し、そのドキュメントをカスタマイズから除外することもできます。  
  
 次の表は、カスタマイズ アセンブリの管理に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|---------|--------------|  
|ドキュメントがドキュメント レベルのカスタマイズの一部であるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> メソッド。|  
|プログラムによって実行時にカスタマイズをドキュメントにアタッチする。<br /><br /> 詳細については、「[方法: マネージ コード拡張機能をドキュメントにアタッチする](../vsto/how-to-attach-managed-code-extensions-to-documents.md)」を参照してください。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> メソッドの 1 つ。|  
|プログラムによって実行時にドキュメントからカスタマイズを削除する。<br /><br /> 詳細については、「[方法: マネージ コード拡張をドキュメントから削除する](../vsto/how-to-remove-managed-code-extensions-from-documents.md)」を参照してください。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> メソッド。|  
|ドキュメントに関連付けられている配置マニフェストの URL を取得する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> プロパティ。|  
  
## 参照  
 [方法: マネージ コード拡張機能をドキュメントにアタッチする](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [方法: マネージ コード拡張をドキュメントから削除する](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)  
  
  