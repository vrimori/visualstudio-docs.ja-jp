---
title: "Vspackage でリソース |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Vspackage でのリソース
ネイティブ UI、サテライト Dll マネージ サテライト Dll、またはマネージ VSPackage 自体では、ローカライズされたリソースを埋め込むことができます。  
  
 一部のリソースは、Vspackage に埋め込むことはできません。 次のマネージ型を埋め込むことができます。  
  
-   文字列  
  
-   パッケージ読み込みキー (これはもある文字列)  
  
-   [ツール] ウィンドウ アイコン  
  
-   コンパイル済みのコマンド テーブルの出力 (CTO) ファイル  
  
-   最高技術責任者のビットマップ  
  
-   コマンドラインのヘルプ  
  
-   ダイアログ ボックスのデータについて  
  
 管理されているパッケージにリソースのリソース ID を選択します。 例外は、最高技術責任者ファイルは、CTMENU という名前です。 最高技術責任者ファイルは、リソース テーブルに表示する必要があります、`byte[]`です。 その他のすべてのリソース項目は、型で識別されます。  
  
 使用することができます、<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>に示すために属性[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]マネージ リソースが使用できることです</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>。  
  
 [!code-cs[VSSDKResources&1;](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources&1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 設定<xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>こうすることを示します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>を使用して、たとえば、リソースについては、検索するときに、アンマネージ サテライト Dll を無視する必要があります</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> 場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が同一のリソース ID を持つ&2; つ以上のリソースを検出したが見つかった最初のリソースを使用します。  
  
## <a name="example"></a>例  
 次の例は、ツール ウィンドウ アイコンのマネージ表現です。  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 次の例では、最高技術責任者のバイト配列、CTMENU という名前を埋め込む方法を示します。  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>実装に関するメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可能な限り VSPackages の遅延読み込みします。 VSPackage で CTO ファイルに埋め込むを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]コマンドがマージされたテーブルを作成する場合はセットアップ中にメモリ内でこのようなすべての VSPackages を読み込む必要があります。 VSPackage でコードを実行することがなく、メタデータを確認するには、VSPackage からリソースを抽出できます。 パフォーマンスの低下が最小限で済むため、VSPackage ではこの時点で初期化されていません。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]セットアップ後に VSPackage からリソースを要求、パッケージが既に読み込まれ、初期化する可能性、パフォーマンスの低下が最小限で済むようにします。  
  
## <a name="see-also"></a>関連項目  
 [マネージ VSPackages](../../misc/managed-vspackages.md)   
 [Vspackage を管理します。](../../extensibility/managing-vspackages.md)   
 [MFC アプリケーションのローカライズされたリソース: サテライト Dll](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [マネージ VSPackage](../../misc/managed-vspackages.md)
