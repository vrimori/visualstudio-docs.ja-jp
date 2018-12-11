---
title: VSPackage のインストール ディレクトリの選択 |Microsoft Docs
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
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 385877b8a682574946bfd43e1e51acd771d00a2b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775174"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>VSPackage のインストール ディレクトリの選択
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage とそのサポート ファイルは、ユーザーのファイル システム上にある必要があります。 場所は、VSPackage の管理または非管理対象、サイド バイ サイド バージョン管理スキームとユーザーの選択かどうかによって異なります。  
  
## <a name="unmanaged-vspackages"></a>アンマネージ Vspackage  
 アンマネージ VSPackage は、任意の場所にインストール可能な COM サーバーです。 その登録情報は、その場所を正確に反映する必要があります。 インストーラーのユーザー インターフェイス (UI) では、サブディレクトリとして ProgramFilesFolder Windows インストーラー プロパティの既定の場所を提供する必要があります。 例えば:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\  
  
 小規模なブート パーティションを保持するユーザーに対応する既定のディレクトリを変更し、別のボリューム上のアプリケーションやツールをインストールするユーザーを許可する必要があります。  
  
 を、サイド バイ サイドでパターンがバージョン管理 VSPackage を使用する場合は、さまざまなバージョンを格納するサブディレクトリを使用できます。 例えば:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>マネージド VSPackage  
 マネージ Vspackage は、任意の場所にもインストールできます。 ただし、常にグローバル アセンブリ キャッシュ (GAC) にアセンブリの読み込み時間を短縮するインストールを検討してください。 マネージ Vspackage は、アセンブリの厳密な名前では常に、GAC にインストールするので、厳密な名前の署名の検証は、インストール時にのみ、です。 ファイル システムに別の場所にインストールされている厳密な名前付きアセンブリの署名に読み込まれるたびに検証が必要です。 マネージ Vspackage を GAC にインストールするときに使用 regpkg ツールの **/assembly**アセンブリの厳密な名前を指すレジストリ エントリを記述するスイッチ。  
  
 マネージ Vspackage を GAC 以外の場所にインストールする場合は、アンマネージ Vspackage 用に指定されたディレクトリ階層を選択する以前のアドバイスに従います。 Regpkg ツールの使用 **/codebase** VSPackage アセンブリのパスを指すレジストリ エントリを記述するスイッチ。  
  
 詳細については、次を参照してください。[の登録および登録を解除する Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)します。  
  
## <a name="satellite-dlls"></a>サテライト Dll  
 慣例により、VSPackage がサテライト Dll: 特定のロケールのリソースを含んでいる-VSPackage のディレクトリのサブディレクトリにあります。 サブディレクトリでは、ロケール ID (LCID) の値に対応します。  
  
 [Vspackage の管理](../../extensibility/managing-vspackages.md)レジストリ エントリが場所を制御することを示します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]実際には、VSPackage の検索はサテライト DLL。 ただし、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] LCID 値を次の順序でのという名前のサブディレクトリでは、サテライト DLL を読み込もうとします。  
  
1. 既定の LCID (VS LCID 英語 \1033 など)  
  
2. 既定のサブ言語の LCID 既定値です。  
  
3. システム既定の LCID。  
  
4. 既定のサブ言語とシステムの既定の LCID。  
  
5. 米国英語 (. \1033 または。 \0x409)。  
  
   VSPackage DLL は、リソースとそれに SatelliteDll\DllName レジストリのエントリ ポイントが含まれる場合[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]上記の順序でそれらを読み込もうとします。  
  
## <a name="see-also"></a>関連項目  
 [共有およびバージョン管理 Vspackage の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Vspackage の管理](../../extensibility/managing-vspackages.md)   
 [Managed Package の登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

