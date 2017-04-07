---
title: "相互運用機能アセンブリのコマンド ハンドラーを登録する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 774266bbcd64e87229f8f97626cdff1462b27fcb
ms.lasthandoff: 04/05/2017

---
# <a name="registering-interop-assembly-command-handlers"></a>相互運用機能アセンブリのコマンド ハンドラーを登録します。
VSPackage に登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) は、そのコマンドを正しくルーティングされるようにします。  
  
 手動で編集するか、レジストラー (.rgs) ファイルを使用して、レジストリを更新できます。 詳細については、次を参照してください。[レジストラー スクリプトの作成](/cpp/atl/creating-registrar-scripts)です。  
  
 Managed Package Framework (MPF)<xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>クラス</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>を使用してこの機能を提供します。  
  
 [コマンドの表形式の参照](http://msdn.microsoft.com/en-us/09e9c6ef-9863-48de-9483-d45b7b7c798f)のリソースがアンマネージ サテライト UI dll に配置されます。  
  
## <a name="command-handler-registration-of-a-vspackage"></a>VSPackage のコマンド ハンドラーの登録  
 ユーザー インターフェイス (UI) のハンドラーとして機能する VSPackage のベースのコマンドは、VSPackage にちなんだ名前のレジストリ エントリを必要と`GUID`です。 このレジストリ エントリでは、VSPackage の UI リソース ファイルとそのファイル内のメニュー リソースの場所を指定します。 レジストリ エントリ自体が HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio 下にある\\*\<バージョン >*\Menus、場所*\<バージョン >*のバージョンは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、たとえば 9.0 です。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio のルート パス\\*\<バージョン >*代替で上書きすることができますルートの場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]シェルを初期化します。 ルート パスの詳細については、次を参照してください。 [Windows インストーラーで Vspackage をインストールする](../../extensibility/internals/installing-vspackages-with-windows-installer.md)です。  
  
### <a name="the-ctmenu-resource-registry-entry"></a>CTMENU のリソースのレジストリ エントリ  
 レジストリ エントリの構造です。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> は、 `GUID` {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX} の形式で、VSPackage のです。  
  
 *\<リソース情報に対して >*コンマで区切られた 3 つの要素で構成されます。 これらの要素は、次の順序で。  
  
 \<*リソース DLL へのパス*>、 \<*メニュー リソース ID*>、 \<*メニュー バージョン*>  
  
 次の表のフィールドの\<*リソース情報に対して*> です。  
  
|要素|説明|  
|-------------|-----------------|  
|\<*リソース DLL へのパス*>|これは空白のままであることを示す、VSPackage のリソース DLL を使用するし、リソース、メニュー リソースを含む DLL への完全パスは (指定されたとおり、VSPackage 自体が登録されているパッケージ サブキー)。<br /><br /> このフィールドは空白になります。|  
|\<*メニュー リソース ID*>|これはのリソース ID、`CTMENU`からがコンパイルされると、VSPackage のすべての UI 要素が含まれるリソース、 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)ファイル。|  
|\<*メニューのバージョン*>|これは、バージョンとして使用する数値、`CTMENU`リソース。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]内容を再マージする必要があるかどうかを決定する値を使用して、`CTMENU`すべてのキャッシュを持つリソース`CTMENU`リソース。 Devenv setup コマンドを実行することによってを再マージが発生します。<br /><br /> この値は最初に 1 に設定、後で変更されるたびにインクリメントされます、`CTMENU`リソースを再マージが発生する前にします。|  
  
### <a name="example"></a>例  
 リソースのエントリのいくつかの例を次に示します。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [相互運用機能アセンブリを使用するコマンドとメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
