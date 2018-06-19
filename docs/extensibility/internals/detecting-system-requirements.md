---
title: システム要件の検出 |Microsoft ドキュメント
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
ms.openlocfilehash: 5e98235bd224876b00714e1f71210ea69cb6faff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128705"
---
# <a name="detecting-system-requirements"></a>システム要件の検出
Visual Studio がインストールされていない場合、VSPackage は機能できません。 Microsoft Windows インストーラーを使用して、VSPackage のインストールを管理する場合は、Visual Studio がインストールされているかどうかを検出するためにインストーラーを構成できます。 システムを調べ、その他の要件の例に、特定のバージョンの Windows または特定の容量の RAM を構成することもできます。  
  
## <a name="detecting-visual-studio-editions"></a>Visual Studio のエディションを検出します。  
 を Visual Studio のエディションがインストールされているかどうかを判断するには、ことを確認インストールのレジストリ キーの値 (REG_DWORD)、適切なフォルダーでは 1、次の表に記載されています。 Visual Studio のエディションの階層があることに注意してください。  
  
1.  エンタープライズ  
  
2.  2 次元形式  
  
3.  コミュニティ  
  
 "Higher"edition がインストールされていると"lower"の各エディションの場合と同様にこのエディションのレジストリ キーが追加されます。 つまり、Enterprise edition がインストールされている場合の Enterprise、および Professional および Community edition の 1 インストール キーが設定します。 そのためのみにする必要があります「最高」エディションを確認する必要があります。  
  
> [!NOTE]
>  64 ビット バージョンのレジストリ エディターでは、32 ビットのキーは、下に表示 hkey_local_machine \software\wow6432node\\です。 Visual Studio のキーは、下にある HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\です。  
  
|製品|キー|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (統合および分離)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio が実行されている場合を検出します。  
 VSPackage は、VSPackage をインストールすると、Visual Studio が実行している場合、正しく登録できません。 インストーラーは、Visual Studio が実行されているときに検出され、プログラムのインストールを拒否する必要があります。 Windows インストーラーを使用するとしないテーブルのエントリを使用して、このような検出を有効にできます。 代わりに、カスタムの動作を次のように作成する必要があります: を使用して、`EnumProcesses`を devenv.exe プロセスを検出し、起動条件または条件付きで使用されるインストーラー プロパティを設定するか、関数が終了するように求めるダイアログ ボックスを表示Visual Studio です。  
  
## <a name="see-also"></a>関連項目  
 [Windows インストーラーによる VSPackage のインストール](../../extensibility/internals/installing-vspackages-with-windows-installer.md)