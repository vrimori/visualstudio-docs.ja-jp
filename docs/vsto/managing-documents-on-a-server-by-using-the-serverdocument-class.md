---
title: ServerDocument クラスを使用してサーバー上のドキュメントを管理します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e983f4cf1b90150113fcfa33702d85bb41a30924
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939138"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>ServerDocument クラスを使用してサーバー上のドキュメントを管理します。
  使用することができます、`ServerDocument`クラス、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Microsoft Office Word および Microsoft Office Excel がインストールされていない場合でも、ドキュメント レベルのカスタマイズのさまざまな側面を管理します。 実行できる管理タスクは以下のとおりです。  
  
- ドキュメントまたはブックのデータ キャッシュにあるデータへのアクセスおよびそのデータの変更。 詳細については、次を参照してください。[ドキュメントでキャッシュされたデータを扱う](#CachedData)します。  
  
- ドキュメントに関連付けられているカスタマイズ アセンブリの管理。 詳細については、次を参照してください。[ドキュメントのカスタマイズを管理](#CustomizationInfo)します。  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>ServerDocument クラスを理解します。  
 `ServerDocument` クラスは Office がインストールされていないコンピューターでの使用を目的としています。 したがって、このクラスは通常、Office プロジェクトではなく、コンソール プロジェクトや Windows フォーム プロジェクトなどの Office に統合されないアプリケーションで使用します。 使用して、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>クラス、 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll*アセンブリ。  
  
 `ServerDocument` クラスは、[!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] を使用して作成されたドキュメント レベルのカスタマイズの操作に使用できます。  
  
 詳細については、Visual Studio 2010 Tools for Office Runtime および Office 拡張機能、.NET Framework の次を参照してください。 [Visual Studio Tools for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)します。  
  
> [!NOTE]  
>  使用するレガシ アプリケーションがある場合、`ServerDocument`クラス、`Visual Studio Tools for Office`システム (version 3.0 Runtime)、 `Visual Studio Tools for Office` system (version 3.0 runtime) は、アプリケーションを実行しているコンピューターにインストールする必要があります。 `Visual Studio 2010 Tools for Office runtime`これらのアプリケーションを実行することはできません。  
  
##  <a name="CachedData"></a> ドキュメントのキャッシュされたデータを操作します。  
 `ServerDocument` クラスには、カスタマイズされたドキュメント内のデータ キャッシュの操作に使用できるメンバーが用意されています。 キャッシュされたデータの詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)と[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。  
  
 次の表は、キャッシュされたデータの操作に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|ドキュメントにデータ キャッシュがあるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> メソッド。|  
|ドキュメント内のキャッシュされたデータにアクセスする。<br /><br /> 詳細については、次を参照してください。[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)します。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティ。|  
  
##  <a name="CustomizationInfo"></a> ドキュメントのカスタマイズを管理します。  
 `ServerDocument` クラスのメンバーを使用して、ドキュメントに関連付けられているカスタマイズ アセンブリを管理できます。 たとえば、ドキュメントのカスタマイズをプログラムによって削除し、そのドキュメントをカスタマイズから除外することもできます。  
  
 次の表は、カスタマイズ アセンブリの管理に使用できるメンバーを示しています。  
  
|タスク|使用するメンバー|  
|----------|-------------------|  
|ドキュメントがドキュメント レベルのカスタマイズの一部であるかどうかを確認する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> メソッド。|  
|プログラムによって実行時にドキュメントにカスタマイズをアタッチします。<br /><br /> 詳細については、次を参照してください[方法: 添付ドキュメントへのコードの拡張機能の管理。](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> メソッドの 1 つ。|  
|プログラムによって実行時にドキュメントからカスタマイズを削除する。<br /><br /> 詳細については、次を参照してください。[方法: ドキュメントからマネージ コード拡張機能を削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)します。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> メソッド。|  
|ドキュメントに関連付けられている配置マニフェストの URL を取得する。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> プロパティ。|  
  
## <a name="see-also"></a>関連項目  
 [方法: 添付ドキュメントへのコードの拡張機能の管理](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [方法: ドキュメントからマネージ コード拡張機能を削除](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio のツール for Office runtime の概要](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [キャッシュ データ](../vsto/caching-data.md)  
  