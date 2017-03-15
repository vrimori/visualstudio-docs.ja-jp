---
title: "エディターでは、ファイルを開き、プロジェクトに決定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ac16b6f4d8429d328cfd76b8b02cd1620f4a4294
ms.lasthandoff: 02/22/2017

---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>どのエディターが開き、プロジェクト内のファイルを決定します。
ユーザーは、プロジェクト内でファイルを開くときに、最終的に、適切なエディターまたはそのファイルのデザイナーを開いて、ポーリング処理によって、環境が移動します。 環境で採用されている最初の手順は、標準およびカスタム エディターに同じです。 環境では、ファイルを開くときに使用するエディターをポーリングするときに、さまざまな条件を使用し、VSPackage がこの処理中に、環境と連携する必要があります。  
  
 ユーザーが選択すると、**開く**コマンドを**ファイル**] メニューの [を選択し、 `filename`.rtf (またはその他のファイル拡張子が .rtf の) 環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>プロジェクトごとに繰り返し最終的に、ソリューション内のすべてのプロジェクト インスタンスを実装します</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>。 プロジェクトでは、優先順位によって、ドキュメントに対する要求を識別するフラグのセットを返します。 最高の優先順位を使用して、環境を呼び出し、適切な<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>。 ポーリング処理の詳細については[プロジェクトに追加してプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
 その他のファイル プロジェクトでは、他のプロジェクトによって請求されていないすべてのファイルを要求します。 これにより、標準的なエディターで開く前に、カスタム エディターでドキュメントを開くことができます。 環境を呼び出す場合は、その他のファイル プロジェクトでは、ファイルを要求、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを標準的なエディターでファイルを開きます</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。 環境では、.rtf ファイルを処理する&1; つの登録済みのエディターの内部リストを確認します。 この一覧は、次のキーにレジストリに格納されます。  
  
 [Hkey_local_machine \software\microsoft\visualstudio\\<`version`> \Editors\\{`editor factory guid`>} \Extensions]  
  
 環境では、サブキー DocObject をしているオブジェクトの hkey_classes_root \clsid キーでクラス id も確認します。 ファイル拡張子は、そこで見つかった場合、埋め込みバージョンの Microsoft Word など、アプリケーションでは、Visual Studio では、インプレースが作成されます。 これらのドキュメント オブジェクトを実装する複合ファイルである必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>インターフェイス、またはオブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイス</xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>。  
  
 レジストリでは、.rtf ファイルのエディター ファクトリがないかどうかは、環境で、HKEY_CLASSES_ROOT にあるか\\.rtf キーと指定されている、エディターが開きます。 HKEY_CLASSES_ROOT にファイル拡張子が見つからない場合、環境エディターを使用して Visual Studio コア テキストをテキスト ファイルの場合は、ファイルを開きます。  
  
 コアのテキスト エディターに失敗した場合、ファイルがテキスト ファイルでない場合、環境、バイナリ エディターのファイルを使用するに発生します。  
  
 環境が、レジストリの .rtf 拡張機能のエディターを見つけ、このエディター ファクトリを実装する VSPackage が読み込まれます。 環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>新しい VSPackage のメソッドです</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>。 VSPackage 呼び出し`QueryService`の`SID_SVsRegistorEditor`を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>環境とエディター ファクトリを登録するメソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>。  
  
 環境は、現在再チェック .rtf ファイルを新しく登録されたエディター ファクトリの検索に登録されているエディターの内部リストです。 環境の実装を呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを作成するファイル名とビューの種類</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat></xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage></xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
