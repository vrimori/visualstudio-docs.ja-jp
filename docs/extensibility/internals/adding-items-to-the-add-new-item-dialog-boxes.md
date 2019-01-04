---
title: 項目を追加、新しい項目の追加 ダイアログ ボックス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d447090585a2314899bb2d6246c6fb450a9e767d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956050"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>新しい項目の追加 ダイアログ ボックスに項目の追加
項目を追加するプロセス、**新しい項目の追加**レジストリ キー ダイアログ ボックスを起動します。 次のレジストリ エントリのように、 **AddItemTemplates**セクションには、どの項目で利用できるように、ディレクトリの名前とパスが含まれています、**新しい項目の追加** ダイアログ ボックスが配置されます。  

> [!NOTE]
>  コード セグメントの直後に続くテーブルには、レジストリ エントリに関する追加情報が含まれています。  

 このセクションでは、下にある**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**します。

 最初の GUID です。 この種類のプロジェクトの CLSID2 つ目の GUID では、項目の追加テンプレートの登録済みのプロジェクトの種類を示します。  

 **\\{C061DB26-5833-11D2-96F5-000000000000}\\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** 6 = 

 **TemplatesDir** = \\&lt;Visual Studio SDK インストール パス&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\&lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** dword:00000064 を =


| 名前 | 型 | データ (から *.rgs*ファイル) | 説明 |
|------------------|-----------| - | - |
| @ (既定値) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY % | リソース ID を**項目の追加**テンプレート。 |
| Val TemplatesDir | REG_SZ | %Template_path\\&lt;SomeProjectItems&gt; | ダイアログ ボックスに表示されるプロジェクト項目のパス、**新しい項目の追加**ウィザード。 |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | ツリー ノードに表示されるファイルの並べ替え順序を決定、**新しい項目の追加** ダイアログ ボックス。 |

> [!NOTE]
>  Visual c# および Visual Basic プロジェクトの種類の GUID は次のとおりです。 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 表示されているディレクトリ**TemplatesDir**、これは *%template_path\\&lt;SomeProjectItems&gt;* の左側にあるノードには、**追加[新しい項目の**] ダイアログ ボックスのツリーです。 ツリー内の他の要素は、そのルート ディレクトリ内のサブディレクトリに基づいています。 ファイルをプロジェクトに追加できるはの右側のウィンドウ内の項目、**新しい項目の追加** ダイアログ ボックス。  

 通常、このフォルダーは HTML テンプレートなど、プロジェクトのテンプレート ファイルを含めるまたは *.cpp*ファイル、および *.vsz*ウィザードを開始するためのファイル。 アイテムの表示方法を制御するには、含める *.vsdir*ファイルのディレクトリ名とアイコンをローカライズします。 ローカライズされた文字列がこのノードを表す ダイアログ ボックスに表示されるキャプション、**新しい項目の追加** ダイアログ ボックスのツリーです。  

 ただし、すべてが 1 つである必要はない *.vsdir*ファイル。 1 つできます *.vsdir*ディレクトリ内のすべての項目のファイル。 詳細については、次を参照してください。[ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)と[テンプレート ディレクトリの説明 (.vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)します。  

> [!NOTE]
>  *.Vsdir*テンプレート ディレクトリ内のファイルは省略可能です。 プロジェクト要素をディレクトリに置きで表示したい場合、**新しい項目の追加** ダイアログ ボックスで指定したテンプレートのディレクトリでそのファイルを配置することができます、 **TemplatesDir**ステートメント。 ファイルは、の右側のウィンドウに表示されますが、**新しい項目の追加**そのプロジェクトのダイアログ ボックス。 ただし、ファイルまたはアイコンのローカライズされたキャプションを表示する場合は、する必要がありますが含まれている、少なくとも *.vsdir*テンプレート ディレクトリ内のファイル。  

## <a name="group-project-items"></a>プロジェクト項目をグループ化  
 テンプレートのグループで、フォルダーを格納するかどうか、**新しい項目の追加** ダイアログ ボックスのツリーで、項目を含むルート テンプレートのディレクトリの下のサブディレクトリがあります。 ときに、**新しい項目の追加** ダイアログ ボックスがユーザーに表示されるはサブフォルダーを参照してからそれらのプロジェクト要素を選択できるようにもします。  

 ツリー ノードの他の要素を基準としてツリーにこのテンプレートのディレクトリを作成する場所のコード セグメントでの並べ替えの優先順位を決定します。 **新しい項目の追加**ダイアログ ボックスで、並べ替えの優先順位 ダイアログ ボックスで、正しい位置に項目が表示されますようにを含める必要のあるすべてです。  

 実装することも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>インターフェイスに表示される内容をフィルター処理する、**新しい項目の追加** ダイアログ ボックス。 このインターフェイスを実装すると、ことができますを設定する 1 つのテンプレートのディレクトリを含む、たとえば、ディスク上のテンプレートとウィザードの 50 個のファイル。 この方法で、1 つのプロジェクトの種類、別の種類のプロジェクトに属している他の 30 個のファイルと、一般的な種類のプロジェクトで使用できるすべてのファイルに属している 20 個のファイルの種類のプロジェクトもかまいません。 テンプレートを作成するプロジェクトによって、この方法では、異なる一連のテンプレート ファイルを表示できます。  

 たとえば、Visual Basic プロジェクトで、Web プロジェクトとクライアント プロジェクトがあります。 Web フォームは、役に立つアイテムをクライアント プロジェクトに追加して、windows フォームは、Web サーバー プロジェクトに追加する役に立つアイテムではありません。 そのため、両方の種類のプロジェクトのすべてのファイルを含む 1 つのテンプレートのディレクトリを作成できます。 その後、実装することによって<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>が表示されないプロジェクトまたはプロジェクトのプロジェクト設定の種類に基づいて項目を非表示にすることができます。  

## <a name="filter-project-items"></a>プロジェクト項目をフィルター処理  
 `IVsFilterAddProjectItemDlg2` ツリー (左側) とプロジェクト ファイル (右側のウィンドウ) で要素の次の方法でフィルター処理を提供します。  

- ローカライズされた名前で (に含まれているダイアログ ボックスに表示されるキャプション、 *.vsdir*ファイル) によって提供される`IVsFilterAddProjectItemDlg`します。  

- ディスク上のファイルおよびフォルダーの実際の名前で (ローカライズされていない-ありません *.vsdir*ファイル) によって提供される`IVsFilterAddProjectItemDlg`します。  

- カテゴリ別にによって提供される`IVsFilterAddProjectItemDlg2`します。  

  カテゴリでフィルター処理、する内の項目にカテゴリ文字列を指定、 *.vsdir*ファイルなど、 *Web フォーム*または*クライアント アイテム*Visual Basic でします。 ダイアログ ボックスのコードからのカテゴリ分類を取得し、 *.vsdir*ファイルに渡します。 実装にその情報を渡すことができますし、`IVsFilterAddProjectItemDlg2`をフィルター処理、**新しい項目の追加**カテゴリ別のダイアログ ボックス。 クライアントの Win32 アプリケーションの場合、Web ページの項目をフィルターすることもできます。 また、どの[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]Microsoft Foundation Classes (MFC) またはアクティブ テンプレート ライブラリ (ATL) の項目として項目をタグ付けします。 これらの項目を識別するときに、プロジェクト システムは、システムにカテゴリと分類に基づくフィルターを選択できるように、独自の分類を定義できます。  

  このフィルターの機能を実装する場合は、非表示にするすべての項目のテーブルにマップするはありません。 単に項目の種類に分類し、分類を配置できます、 *.vsdir*ファイルまたはファイル。 インターフェイスを実装することによって、特定の分類している項目のいずれかが非表示できます。 これにより、内の項目を行うことができます、**新しい項目の追加**プロジェクト内の状態に基づいて、ダイアログ ボックス動的です。  

## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトと項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [プロジェクトの拡張に通常使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [テンプレート ディレクトリの説明 (.vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)