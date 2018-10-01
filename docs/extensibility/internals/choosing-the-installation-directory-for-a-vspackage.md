---
title: VSPackage のインストール ディレクトリの選択 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e32f2581e4980feebbbecb3cc8e7aa98bfeb670
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370953"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>VSPackage のインストール ディレクトリを選択します。
VSPackage とそのサポート ファイルは、ユーザーのファイル システム上にある必要があります。 場所は、VSPackage の管理または非管理対象、サイド バイ サイド バージョン管理スキームとユーザーの選択かどうかによって異なります。  
  
## <a name="unmanaged-vspackages"></a>アンマネージ Vspackage  
 アンマネージ VSPackage は、任意の場所にインストール可能な COM サーバーです。 その登録情報は、その場所を正確に反映する必要があります。 インストーラーのユーザー インターフェイス (UI) では、サブディレクトリとして既定の場所を指定する必要があります、 `ProgramFilesFolder` Windows インストーラー プロパティの値。 例えば:  
  
*&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\V1.0\\*
  
 小規模なブート パーティションを保持するユーザーに対応する既定のディレクトリを変更し、別のボリューム上のアプリケーションやツールをインストールするユーザーを許可する必要があります。  
  
 を、サイド バイ サイドでパターンがバージョン管理 VSPackage を使用する場合は、さまざまなバージョンを格納するサブディレクトリを使用できます。 例えば:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*
  
 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*
  
## <a name="managed-vspackages"></a>マネージド VSPackage  
 マネージ Vspackage は、任意の場所にもインストールできます。 ただし、常にグローバル アセンブリ キャッシュ (GAC) にアセンブリの読み込み時間を短縮するインストールを検討してください。 マネージ Vspackage は、アセンブリの厳密な名前では常に、GAC にインストールするので、厳密な名前の署名の検証は、インストール時にのみ、です。 ファイル システムに別の場所にインストールされている厳密な名前付きアセンブリの署名に読み込まれるたびに検証が必要です。 マネージ Vspackage を GAC にインストールするときに使用 regpkg ツールの **/assembly**アセンブリの厳密な名前を指すレジストリ エントリを記述するスイッチ。  
  
 マネージ Vspackage を GAC 以外の場所にインストールする場合は、アンマネージ Vspackage 用に指定されたディレクトリ階層を選択する以前のアドバイスに従います。 Regpkg ツールの使用 **/codebase** VSPackage アセンブリのパスを指すレジストリ エントリを記述するスイッチ。  
  
 詳細については、次を参照してください。[を登録し、Vspackage の登録解除](../../extensibility/registering-and-unregistering-vspackages.md)します。  
  
## <a name="satellite-dlls"></a>サテライト Dll  
 慣例によりは、VSPackage のサブディレクトリに置かれてサテライト Dll は、特定のロケールのリソースを含む、 *VSPackage*ディレクトリ。 サブディレクトリでは、ロケール ID (LCID) の値に対応します。  
  
 [管理 Vspackage](../../extensibility/managing-vspackages.md)記事では、レジストリ エントリが場所を制御することを示します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実際には、VSPackage の検索はサテライト DLL。 ただし、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] LCID 値を次の順序でのという名前のサブディレクトリでは、サテライト DLL を読み込もうとします。  
  
1.  既定の LCID (Visual Studio の LCID たとえば、 *\1033*英語)。  
  
2.  既定のサブ言語の LCID 既定値です。  
  
3.  システム既定の LCID。  
  
4.  既定のサブ言語とシステムの既定の LCID。  
  
5.  米国英語 (*. \1033*または *. \0x409*)。  
  

VSPackage DLL にリソースが含まれている場合、 **SatelliteDll\DllName**レジストリ エントリが指す、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]それらを上記の順序で読み込みを試みます。  
  
## <a name="see-also"></a>関連項目  
 [共有およびバージョン管理 Vspackage を選択します。](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Vspackage を管理します。](../../extensibility/managing-vspackages.md)   
 [パッケージの登録を管理します。](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)