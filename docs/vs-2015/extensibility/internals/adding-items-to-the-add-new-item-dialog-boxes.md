---
title: 項目を追加、新しい項目の追加 ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6d45431d2d6757169c225136620124d94a6e75dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223107"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>[新しい項目の追加] ダイアログ ボックスへの項目の追加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

項目を追加するプロセス、**新しい項目の追加**レジストリ キー ダイアログ ボックスを起動します。 使用できる項目のディレクトリの名前とパスには、次のレジストリ エントリのように、AddItemTemplates セクションに含まれています、**新しい項目の追加** ダイアログ ボックスが配置されます。  
  
> [!NOTE]
>  コード セグメントの直後に続くテーブルには、レジストリ エントリに関する追加情報が含まれています。  
  
 このセクションでは、[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects] の下にあります。  
  
 最初の GUID です。 この種類のプロジェクトの CLSID2 つ目の GUID では、項目の追加テンプレートの登録済みのプロジェクトの種類を示します。  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} {ACEF4EB2-57CF-11D2-96F4-000000000000} \AddItemTemplates\TemplateDirs\ \1  
  
 @="#6"  
  
 "TemplatesDir「=」\<Visual Studio SDK インストール パス\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority"dword:00000064 を =  
  
|名前|型|(.Rgs ファイル) からのデータ|説明|  
|----------|----------|-----------------------------|-----------------|  
|@ (既定値)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|リソース ID を**項目の追加**テンプレート。|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\SomeProjectItems|ダイアログ ボックスに表示されるプロジェクト項目のパス、**新しい項目の追加**ウィザード。|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|ツリー ノードに表示されるファイルの並べ替え順序を決定、**新しい項目の追加** ダイアログ ボックス。|  
  
> [!NOTE]
>  Visual c# および Visual Basic プロジェクトの種類の GUID は、次のように:[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 ディレクトリにある % TEMPLATE_PATH%\SomeProjectItems TemplateDirs はの左側にあるノードが表示されている、**新しい項目の追加** ダイアログ ボックスのツリーです。 ツリー内の他の要素は、そのルート ディレクトリ内のサブディレクトリに基づいています。 ファイルをプロジェクトに追加できるはの右側のウィンドウ内の項目、**新しい項目の追加** ダイアログ ボックス。  
  
 通常、このフォルダーは、テンプレート HTML または .cpp ファイルなど、プロジェクトのテンプレート ファイルとウィザードを起動する .vsz ファイルに格納されます。 アイテムの表示方法を制御するには、ディレクトリ名とアイコンのローカライズ .vsdir ファイルも含めることができます。 ローカライズされた文字列は、この新しい項目の追加 ダイアログのツリー ノードを表す ダイアログ ボックスに表示されるキャプションです。  
  
 ただし、1 つの .vsdir ファイルにすべてのものがある必要はありません。 ディレクトリ内のすべての項目の 1 つの .vsdir ファイルがあることができます。 詳細については、次を参照してください。[ウィザード (します。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)と[テンプレート ディレクトリの説明 (します。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)します。  
  
> [!NOTE]
>  テンプレートのディレクトリに .vsdir ファイルは省略可能です。 プロジェクト要素をディレクトリに置きで表示したい場合、**新しい項目の追加**ダイアログ ボックスで、TemplatesDir ステートメントで指定されたテンプレートのディレクトリでそのファイルを配置することができます。 ファイルは、の右側のウィンドウに表示されますが、**新しい項目の追加**そのプロジェクトのダイアログ ボックス。 ただし、ファイルまたはアイコンのローカライズされたキャプションを表示する場合は、テンプレート ディレクトリに .vsdir ファイルを 1 つ以上を含める必要があります。  
  
## <a name="grouping-project-items"></a>プロジェクト項目のグループ化  
 テンプレートのグループで、フォルダーを格納するかどうか、**新しい項目の追加** ダイアログ ボックスのツリーで、項目を含むルート テンプレートのディレクトリの下のサブディレクトリがあります。 ときに、**新しい項目の追加** ダイアログ ボックスがユーザーに表示されるはサブフォルダーを参照してからそれらのプロジェクト要素を選択できるようにもします。  
  
 ツリー ノードの他の要素を基準としてツリーにこのテンプレートのディレクトリを作成する場所のコード セグメントでの並べ替えの優先順位を決定します。 **新しい項目の追加**ダイアログ ボックスで、並べ替えの優先順位 ダイアログ ボックスで、正しい位置に項目が表示されますようにを含める必要のあるすべてです。  
  
 実装することも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>インターフェイスに表示される内容をフィルター処理する、**新しい項目の追加** ダイアログ ボックス。 このインターフェイスを実装すると、ことができますを設定する 1 つのテンプレートのディレクトリを含む、たとえば、ディスク上のテンプレートとウィザードの 50 個のファイル。 この方法で、1 つのプロジェクトの種類、別の種類のプロジェクトに属している他の 30 個のファイルと、一般的な種類のプロジェクトで使用できるすべてのファイルに属している 20 個のファイルの種類のプロジェクトもかまいません。 テンプレートを作成するプロジェクトによって、この方法では、異なる一連のテンプレート ファイルを表示できます。  
  
 たとえば、Visual Basic プロジェクトで、Web プロジェクトとクライアント プロジェクトがあります。 Web フォームは、役に立つアイテムをクライアント プロジェクトに追加して、windows フォームは、Web サーバー プロジェクトに追加する役に立つアイテムではありません。 そのため、両方の種類のプロジェクトのすべてのファイルを含む 1 つのテンプレートのディレクトリを作成できます。 実装することによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>が表示されないプロジェクトまたはプロジェクトのプロジェクト設定の種類に基づいて項目を非表示にすることができます。  
  
## <a name="filtering-project-items"></a>プロジェクト項目をフィルター処理  
 `IVsFilterAddProjectItemDlg2` ツリー (左側) とプロジェクト ファイル (右側のウィンドウ) で要素の次の方法でフィルター処理を提供します。  
  
-   によって提供されるローカライズされた名前 (.vsdir ファイルに含まれるダイアログ ボックスに表示されるキャプション) によって`IVsFilterAddProjectItemDlg`します。  
  
-   ディスク上のファイルおよびフォルダーの実際の名前で (ローカライズされていない-.vsdir ファイルがありません) によって提供される`IVsFilterAddProjectItemDlg`します。  
  
-   カテゴリ別にによって提供される`IVsFilterAddProjectItemDlg2`します。  
  
 カテゴリでフィルター処理するには、Visual Basic では"クライアント item"または「Web フォーム」など、.vsdir ファイル内の項目にカテゴリ文字列を指定します。 ダイアログ ボックスのコードは、.vsdir ファイルからのカテゴリ分類を取得しに渡します。 実装にその情報を渡すことができますし、`IVsFilterAddProjectItemDlg2`をフィルター処理、**新しい項目の追加**カテゴリ別のダイアログ ボックス。 クライアントの Win32 アプリケーションの場合、Web ページの項目をフィルターすることもできます。 また、どの[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]Microsoft Foundation Classes (MFC) またはアクティブ テンプレート ライブラリ (ATL) の項目として項目をタグ付けします。 これらの項目を識別するときに、プロジェクト システムは、システムにカテゴリと分類に基づくフィルターを選択できるように、独自の分類を定義できます。  
  
 このフィルターの機能を実装する場合は、非表示にするすべての項目のテーブルにマップするはありません。 単に、項目の種類に分類し、.vsdir ファイルまたはファイルに分類できます。 インターフェイスを実装することによって、特定の分類している項目のいずれかが非表示できます。 これにより、内の項目を行うことができます、**新しい項目の追加**プロジェクト内の状態に基づいて、ダイアログ ボックス動的です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [プロジェクトの拡張に通常使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [テンプレート ディレクトリの説明 (します。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)

