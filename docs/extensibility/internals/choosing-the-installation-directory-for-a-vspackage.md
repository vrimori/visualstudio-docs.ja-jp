---
title: VSPackage のインストール ディレクトリの選択 |Microsoft ドキュメント
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
ms.openlocfilehash: 564a184e8b3907f5a61bccc26cfbafa8d2cf8e67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134442"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>VSPackage のインストール ディレクトリの選択
VSPackage とそのサポート ファイルは、ユーザーのファイル システム上でなければなりません。 場所は、VSPackage がかどうかの管理や、アンマネージ、サイド バイ サイドのバージョン管理スキーム、およびユーザーの選択によって異なります。  
  
## <a name="unmanaged-vspackages"></a>アンマネージ Vspackage  
 アンマネージ VSPackage は、任意の場所にインストール可能な COM サーバーです。 その登録情報では、その場所を正確に反映する必要があります。 インストーラーのユーザー インターフェイス (UI) をサブディレクトリとして ProgramFilesFolder Windows インストーラー プロパティの既定の場所を提供する必要があります。 例えば:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\  
  
 小さなブート パーティションを保持するユーザーに対応する既定のディレクトリを変更し、別のボリューム上のアプリケーションおよびツールをインストールするユーザーを許可する必要があります。  
  
 サイド バイ サイド スキームは、バージョン管理された VSPackage を使用している場合は、異なるバージョンを格納するサブディレクトリを使用できます。 例えば:  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 [ProgramFilesFolder]MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>マネージ VSPackage  
 マネージ Vspackage は、任意の場所にインストールすることもできます。 ただし、常にグローバル アセンブリ キャッシュ (GAC) アセンブリの読み込み時間を短縮するへのインストールを検討してください。 マネージ Vspackage は、厳密な名前付きアセンブリでは常に、GAC にインストールするので、厳密な名前の署名の検証がインストール時にのみを取ることです。 ファイル システムで他の場所にインストールされている厳密な名前のアセンブリの署名が読み込まれるたびに検証が必要です。 マネージ Vspackage を GAC にインストールするときに使用 regpkg ツールの **/assembly**アセンブリの厳密な名前を指すレジストリ エントリを記述するスイッチです。  
  
 GAC 以外の場所にマネージ Vspackage をインストールする場合は、以前アドバイス アンマネージ Vspackage 用のディレクトリ階層を選択に従ってください。 Regpkg ツールの使用 **/codebase** VSPackage アセンブリのパスを指すレジストリ エントリを記述するスイッチです。  
  
 詳細については、次を参照してください。[の登録および登録解除 Vspackage](../../extensibility/registering-and-unregistering-vspackages.md)です。  
  
## <a name="satellite-dlls"></a>サテライト Dll  
 規則では、VSPackage のサテライト Dll — 特定のロケールのリソースを含んでいる: VSPackage のディレクトリのサブディレクトリにあります。 サブディレクトリは、ロケール ID (LCID) の値に対応します。  
  
 [Vspackage を管理する](../../extensibility/managing-vspackages.md)レジストリ エントリが場所を制御することを示す[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]実際には、VSPackage の検索サテライト DLL です。 ただし、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]次の順序で、LCID 値をという名前のサブディレクトリでは、サテライト DLL の読み込みを試みます。  
  
1.  既定の LCID (VS LCID 英語用 \1033 など)  
  
2.  既定のサブ言語の LCID 既定値です。  
  
3.  システム既定の LCID。  
  
4.  既定のサブ言語でシステムの既定 LCID。  
  
5.  米国英語 (. \1033 または。 \0x409)。  
  
 VSPackage DLL には、リソースと、SatelliteDll\DllName レジストリのエントリ ポイントが含まれている場合[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]が上記の順序でそれらを読み込もうとします。  
  
## <a name="see-also"></a>関連項目  
 [共有とバージョン管理された Vspackage の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Vspackage の管理](../../extensibility/managing-vspackages.md)   
 [マネージ パッケージの登録](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)