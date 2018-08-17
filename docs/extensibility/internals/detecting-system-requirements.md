---
title: システム要件の検出 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a794391001934164e52bdd73d940cb73ff3b5f3b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500083"
---
# <a name="detect-system-requirements"></a>システム要件を検出します。
Visual Studio がインストールされていない場合、VSPackage は機能できません。 Microsoft Windows インストーラーを使用して、VSPackage のインストールを管理する場合は、Visual Studio がインストールされているかどうかを検出するインストーラーを構成できます。 など、システムの他の要件を確認して、特定のバージョンの Windows または特定の容量の RAM を構成することもできます。  
  
## <a name="detect-visual-studio-editions"></a>Visual Studio のエディションを検出します。  
 Visual Studio のエディションがインストールされているかどうかを判断することを確認の値、**インストール**レジストリ キーが *(REG_DWORD) 1*次の表に一覧表示されていると、適切なフォルダーにします。 Visual Studio のエディションの階層があることに注意してください。  
  
1.  エンタープライズ  
  
2.  2 次元形式  
  
3.  コミュニティ  
      
新しいエディションがインストールされているときにそのエディション用のレジストリ キーが以前のエディションの場合とでも追加されます。 つまり、Enterprise edition がインストールされて、**インストール**にキーが設定されている*1*の Enterprise、および Professional および Community エディション。 そのため、必要な最新のエディションのみを確認する必要があります。  
  
> [!NOTE]
>  レジストリ エディターの 64 ビット バージョンで 32 ビットのキーが表示される**hkey_local_machine \software\wow6432node\\**します。 Visual Studio のキーは、 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**します。  
  
|製品|キー|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (統合シェルと分離)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Visual Studio が実行されていることを検出します。  
 VSPackage は、VSPackage のインストール時に Visual Studio が実行されている場合、正しく登録できません。 インストーラーは、Visual Studio が実行されているときに検出され、プログラムのインストールを拒否しする必要があります。 Windows インストーラーではテーブルのエントリを使用して、このような検出を有効にできます。 代わりに、カスタムの動作を次のように作成する必要があります使用して、`EnumProcesses`を検出する関数、 *devenv.exe*処理、および起動条件のために使用されるインストーラー プロパティを設定し、か、またはダイアログ ボックスの条件付きで表示。ユーザーを Visual Studio を閉じるように求められます。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)