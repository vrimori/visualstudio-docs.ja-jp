---
title: "項目を追加する、新しい項目の追加 ダイアログ ボックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f7058d097ab3eb6faeb8acf96b98ae6346887361
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>項目を追加する、新しい項目の追加 ダイアログ ボックス
項目を追加するプロセス、**新しい項目の追加**レジストリ キーを持つ ダイアログ ボックスを起動します。 次のレジストリ エントリのように、AddItemTemplates セクション内で使用できるようにする項目のディレクトリの名前とパスの**新しい項目の追加** ダイアログ ボックスが配置されます。  
  
> [!NOTE]
>  すぐに次のコード セグメント テーブルには、レジストリ エントリに関する追加情報が含まれています。  
  
 このセクションでは、[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects] 下にあります。  
  
 最初の GUID がこの型のプロジェクトの CLSID2 番目の GUID では、アイテムの追加テンプレートの登録済みのプロジェクトの種類を示します。  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir「=」\<Visual Studio SDK インストール パス\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority"dword:00000064 を =  
  
|name|型|(.Rgs ファイル) からのデータ|説明|  
|----------|----------|-----------------------------|-----------------|  
|@ (既定値)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|リソース ID**項目の追加**テンプレート。|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\SomeProjectItems|ダイアログ ボックスに表示されるプロジェクト アイテムのパス、**新しい項目の追加**ウィザード。|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|ツリー ノードに表示されるファイルの並べ替え順序を決定、**新しい項目の追加** ダイアログ ボックス。|  
  
> [!NOTE]
>  Visual c# および Visual Basic プロジェクトの種類の GUID は次のように、:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 ある % TEMPLATE_PATH%\SomeProjectItems TemplateDirs がの左側にあるノードでは、ディレクトリが表示されている、**新しい項目の追加** ダイアログ ボックスのツリーです。 ツリー内の他の要素は、そのルート ディレクトリ内のサブディレクトリに基づいています。 ファイルをプロジェクトに追加できるはの右側のウィンドウ内の項目、**新しい項目の追加** ダイアログ ボックス。  
  
 通常、このフォルダーは、テンプレート HTML または .cpp ファイルなど、プロジェクトのテンプレート ファイルとウィザードを開始するためには、すべて .vsz ファイルに格納されます。 アイテムの表示方法を制御するにディレクトリ名とアイコンのローカライズ用 .vsdir ファイルを追加することもできます。 ローカライズされた文字列は、このノード ツリーで、新しい項目の追加 ダイアログを表す ダイアログ ボックスに表示されるキャプションです。  
  
 ただし、1 つの .vsdir ファイルにあるすべてのものにはありません。 1 つの .vsdir ファイル、ディレクトリ内のすべての項目のことができます。 詳細については、次を参照してください。[ウィザード (です。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)と[テンプレート ディレクトリの説明 (です。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)です。  
  
> [!NOTE]
>  テンプレートのディレクトリに .vsdir ファイルは省略できます。 プロジェクトの要素をディレクトリに配置し、内に表示したい場合、**新しい項目の追加**ダイアログ ボックスで、TemplatesDir ステートメントで指定されたテンプレート フォルダーにそのファイルを配置することができます。 ファイルはの右側のペインに表示されます、**新しい項目の追加**そのプロジェクトのダイアログ ボックス。 ただし、ファイルやアイコンのローカライズされたキャプションを表示する場合は、テンプレート ディレクトリに .vsdir の少なくとも 1 つのファイルを含める必要があります。  
  
## <a name="grouping-project-items"></a>プロジェクト項目のグループ化  
 内のフォルダーにテンプレートのグループを記述するかどうか、**新しい項目の追加** ダイアログ ボックスのツリーで、項目を含むルート テンプレート ディレクトリのサブディレクトリにする必要があります。 ときに、**新しい項目の追加** ダイアログ ボックスを表示するユーザーはもサブフォルダーを参照してくださいをそこからプロジェクトの要素を選択できます。  
  
 並べ替えの優先順位のコード例でこのテンプレートのディレクトリが作成されるツリー ノードの他の要素を基準としたツリーを判断します。 **新しい項目の追加**ダイアログ ボックスで、並べ替えの優先順位こと ダイアログ ボックスで、正しい位置に、項目が表示されるようにする必要があります。  
  
 実装することも、<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>インターフェイスに表示される内容をフィルター処理を**新しい項目の追加** ダイアログ ボックス。 このインターフェイスを実装すると、ことができますを設定する 1 つのテンプレートのディレクトリを含む、たとえば、ディスク上のテンプレートとウィザードの 50 のファイル。 この方法で 1 つのプロジェクトの種類、別の種類のプロジェクトに属している他の 30 個のファイルと一般的な種類のプロジェクトで利用可能なすべてのファイルに属している 20 個のファイルを別のプロジェクトの種類を持つことができます。 テンプレートを作成するプロジェクトにより、この方法では、異なるテンプレート ファイルのセットを表示できます。  
  
 たとえば、Visual Basic プロジェクトで、Web プロジェクトとクライアント プロジェクトがあります。 Windows フォームは、Web サーバー プロジェクトに追加する役に立つアイテムと web フォームは、クライアント プロジェクトに追加する役に立つアイテムではありません。 したがって、両方の種類のプロジェクトのすべてのファイルを含む 1 つのテンプレートのディレクトリを作成できます。 実装することによって、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>、プロジェクトまたはプロジェクトのプロジェクト設定の種類に基づいたが表示されない項目を非表示にすることができます。  
  
## <a name="filtering-project-items"></a>プロジェクト項目をフィルター処理  
 `IVsFilterAddProjectItemDlg2`ツリー (左側) とプロジェクト ファイル (右ペイン) で要素の次の方法でフィルター処理について説明します。  
  
-   ローカライズされた名前 (.vsdir ファイルに含まれているダイアログ ボックスに表示されるキャプション) によって提供される`IVsFilterAddProjectItemDlg`です。  
  
-   実際のファイルとディスク上のフォルダー名を使用して (ローカライズされていない — .vsdir ファイルがありません) によって提供される`IVsFilterAddProjectItemDlg`です。  
  
-   によって提供される、カテゴリ別`IVsFilterAddProjectItemDlg2`です。  
  
 カテゴリでフィルタ リングするには、「Web フォーム」など、.vsdir ファイル内のアイテムまたは Visual Basic では「クライアントの項目」カテゴリ文字列を提供します。 ダイアログ ボックスのコードに、.vsdir ファイルからのカテゴリ分類を取得しに渡します。 実装にその情報を渡すことができますし、`IVsFilterAddProjectItemDlg2`をフィルター処理、**新しい項目の追加**カテゴリ ダイアログ ボックス。 クライアントの Win32 アプリケーションの場合、Web ページの項目をフィルターすることもできます。 また、どの[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]Microsoft Foundation Classes (MFC)、またはアクティブ テンプレート ライブラリ (ATL) の項目として項目をタグ付けします。 これらの項目を特定する際に、プロジェクト システムは、システムにカテゴリと分類に基づいてフィルターを選択できるように、独自の分類を定義できます。  
  
 このフィルターの機能を実装する場合、非表示にするすべての項目のテーブルにマップするはありません。 単に項目を型に分類し、.vsdir ファイルまたはファイルの分類を配置できます。 インターフェイスを実装することによって、特定の分類している項目のいずれかが非表示できます。 これにより、内の項目を行うことができます、**新しい項目の追加**プロジェクト内の状態に基づいて、ダイアログ ボックス動的です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトと項目テンプレートの登録](../../extensibility/internals/registering-project-and-item-templates.md)   
 [プロジェクトを拡張する通常使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [テンプレート ディレクトリの説明 (です。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)