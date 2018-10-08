---
title: エディターがプロジェクトでファイルを開きますの決定 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b144b9d380e652857b08733e48d43b5b7609ffd6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546077"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>プロジェクトでのファイルを開くエディターの決定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクトでファイルを開くエディターを決定する](https://docs.microsoft.com/visualstudio/extensibility/internals/determining-which-editor-opens-a-file-in-a-project)します。  
  
プロジェクトでユーザーがファイルを開くと、最終的に、適切なエディターまたはデザイナーがそのファイルを開いて、ポーリング処理によって、環境が移動します。 環境で採用されている最初の手順では、標準とカスタムの両方のエディターに同じです。 環境ではファイルを開くときに使用するエディターをポーリングするときに、さまざまな条件を使用し、VSPackage は、このプロセス中に、環境と調整する必要があります。  
  
 たとえば、ユーザーが選択すると、**オープン**コマンドを**ファイル**] メニューの [を選択し、 `filename`.rtf (またはその他のファイル拡張子が .rtf) 環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>最終的に、ソリューション内のすべてのプロジェクト インスタンスを繰り返し、各プロジェクトの実装です。 プロジェクトでは、優先順位によって、ドキュメントに対する要求を識別するフラグのセットを返します。 最高の優先順位を使用して、環境が呼び出す、適切な<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッド。 ポーリングのプロセスの詳細については[プロジェクトに追加してプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
 その他のファイル プロジェクトでは、他のプロジェクトでは請求されないすべてのファイルを要求します。 これにより、標準のエディターで開く前に、カスタム エディターでドキュメントを開くことができます。 環境を呼び出す場合、その他のファイル プロジェクトには、ファイルが要求を<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを標準のエディターでファイルを開きます。 環境は、.rtf ファイルを処理する 1 つの登録済みのエディターの内部リストを確認します。 この一覧は、レジストリ内で、次のキーにあります。  
  
 [Hkey_local_machine \software\microsoft\visualstudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 環境には、hkey_classes_root \clsid キーをサブキー DocObject を持つ任意のオブジェクトのクラス識別子も確認します。 ファイル拡張子は、そこで見つかった場合埋め込みバージョンの Microsoft Word など、アプリケーションが Visual Studio で、インプレースを作成します。 これらのドキュメント オブジェクトを実装する複合ファイルである必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>インターフェイス、またはオブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイス。  
  
 .Rtf ファイル、レジストリ内のエディター ファクトリがないかどうかは、環境で、HKEY_CLASSES_ROOT にあるか\\.rtf キーと指定エディターが開きます。 HKEY_CLASSES_ROOT のファイル拡張子が見つからない場合、環境はテキスト ファイルの場合は、ファイルを Visual Studio のコアのテキスト エディターを使用します。  
  
 テキストのコア エディターが失敗した場合、ファイルがテキスト ファイルでない場合、環境、バイナリ エディターのファイルを使用するに発生します。  
  
 環境は、レジストリで、エディター .rtf 拡張機能を検索するは、このエディターのファクトリを実装する VSPackage が読み込まれます。 環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>新しい VSPackage のメソッド。 VSPackage 呼び出し`QueryService`の`SID_SVsRegistorEditor`を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>環境とエディターのファクトリを登録するメソッド。  
  
 環境は、現在再チェックの .rtf ファイルを新しく登録されたエディター ファクトリを検索する登録済みのエディターの内部リスト。 環境の実装を呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを作成するファイル名とビューの種類。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

