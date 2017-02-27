---
title: "VSPackage のインストール ディレクトリを選択します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vspackages にある、インストール ディレクトリ"
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# VSPackage のインストール ディレクトリを選択します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage とサポート ファイルはユーザーのファイル システムである必要があります。  場所はVSPackage がマネージまたはアンマネージside\-by\-side でのバージョン管理の設定とユーザーの選択範囲であるかどうかによって異なります。  
  
## アンマネージ VSPackage  
 アンマネージの VSPackage は任意の場所にインストールできる COM サーバーです。  この登録情報を指定する必要が正確に場所を反映します。  インストーラーのユーザー インターフェイスは \(UI\) ProgramFilesFolder の Windows インストーラーのプロパティのサブディレクトリで既定の場所を指定する必要があります。  次に例を示します。  
  
 \[ProgramFilesFolder\] MyCompany \\ \\ \\ MyVSPackageProduct V1.0  
  
 ユーザーが初めてパーティションを保持し別の面積のアプリケーションとツールをインストールするユーザーに対応する既定のディレクトリを変更できないようにする必要があります。  
  
 side\-by\-side でのバージョン管理設定を VSPackage を使用すると異なるバージョンを格納するためにサブディレクトリを使用できます。  次に例を示します。  
  
 \[ProgramFilesFolder\] MyCompany \\ \\ MyVSPackageProduct V1.0 \\ 2002 \\  
  
 \[ProgramFilesFolder\] MyCompany \\ \\ MyVSPackageProduct V1.0 \\ 2003 \\  
  
 \[ProgramFilesFolder\] MyCompany \\ \\ MyVSPackageProduct V1.0 \\ 2005 \\  
  
## マネージ VSPackage  
 マネージ VSPackage は任意の場所にインストールできます。  ただしアセンブリの読み込み時間を短くするにはグローバル アセンブリ キャッシュに \(GAC\) インストール常に検討する必要があります。  マネージ VSPackage が厳密な名前のアセンブリで常にであるためGAC にインストール厳密な名前の署名の検証のインストール時にのみ取得することを意味します。  検証するファイル システム上の他の場所にインストールされて読み込まれるたびに厳密な名前付きアセンブリはの定義が必要です。  GAC のマネージ VSPackage をインストールするとアセンブリの厳密な名前を指すレジストリ エントリを書き込むために regpkg ツールの **\/assembly** スイッチを使用します。  
  
 GAC 以外の場所のマネージ VSPackage をインストールしたディレクトリ階層の任意のアンマネージ VSPackage に対して指定するための推奨事項に従ってください。  VSPackage のアセンブリのパスを指すレジストリ エントリを書き込むために regpkg ツールの **\/codebase** スイッチを使用します。  
  
 詳細については、「[Vspackage の登録と登録解除しています](../../extensibility/registering-and-unregistering-vspackages.md)」を参照してください。  
  
## サテライト DLL  
 規則では特定のロケールのリソースを含む VSPackage のサテライト DLL VSPackage ディレクトリのサブディレクトリ \(あります。  サブディレクトリはロケール ID \(LCID\) の値に対応します。  
  
 [Vspackage を管理します。](../../extensibility/managing-vspackages.md) は [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] がVSPackage のサテライト DLL を検索するレジストリ エントリが設定されていることを示します。  ただし次の順序で LCID 値のという名前のサブディレクトリのサテライト DLL の読み込みを試みます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
1.  既定の LCID \(英語の LCID たとえば \\ 1033 "\)  
  
2.  既定のサブ言語の既定の LCID。  
  
3.  システムの既定の LCID。  
  
4.  既定のサブ言語のシステムの既定の LCID。  
  
5.  英語版  \(英語。  \\ 1033 または。  \\ 0x409\)。  
  
 VSPackage の DLL がそれにリソースと SatelliteDll \\ DllName のレジストリ エントリ ポイントが含まれている場合は[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は上記の順序で読み込みを試みます。  
  
## 参照  
 [共有およびバージョン管理の VSPackages の使い分け](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Vspackage を管理します。](../../extensibility/managing-vspackages.md)   
 [Managed Package Registration](http://msdn.microsoft.com/ja-jp/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)