---
title: "システム要件の検出 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セットアップ、VSPackage"
  - "起動条件"
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 50
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 50
---
# システム要件の検出
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio がインストールされていない機能には、VSPackage を使用しません。 Microsoft Windows インストーラーを使用して、VSPackage のインストールを管理する場合は、Visual Studio がインストールされているかどうかを検出するためにインストーラーを構成できます。 システムの他の要件を次に例をチェックして、特定のバージョンの Windows または特定の容量の RAM を構成することもできます。  
  
## Visual Studio のエディションを検出します。  
 Visual Studio のエディションがインストールされているかどうかを判断するには、ことを確認インストールのレジストリ キーの値 \(REG\_DWORD\) 適切なフォルダー内の 1 次の表に記載されています。 Visual Studio のエディションの階層があることに注意してください。  
  
1.  エンタープライズ  
  
2.  2 次元形式  
  
3.  コミュニティ  
  
 「高」のエディションがインストールされている場合は、"lower"の各エディションの場合と同様にこのエディションのレジストリ キーが追加されます。 つまり、Enterprise edition がインストールされている場合は、インストール キーを 1 Enterprise、および Professional、およびコミュニティ エディションに設定されます。 そのためのみにする必要があります「最高」エディションをチェックする必要があります。  
  
> [!NOTE]
>  レジストリ エディターの 64 ビット バージョンで \\software\\wow6432node\\ \[32 ビットのキーが表示されます。 Visual Studio のキーは、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\ されます。  
  
|製品|キー|  
|--------|--------|  
|Visual Studio Enterprise 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\enterprise|  
|Visual Studio Professional 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\professional|  
|Visual Studio Community 2015|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\community|  
|Visual Studio 2015 Shell \(統合および分離\)|HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell|  
  
## Visual Studio が実行されているときに検出します。  
 VSPackage をインストールすると、Visual Studio が実行している場合、VSPackage を正常に登録できません。 インストーラーは、Visual Studio が実行されているときに検出され、プログラムをインストールし、拒否する必要があります。 Windows インストーラーを使用するとしないテーブルのエントリを使用して、このような検出を有効にできます。 代わりに、カスタム動作を次のように作成する必要があります。 使用する、 `EnumProcesses` devenv.exe プロセスを検出して、起動条件や条件付きで使用されるインストーラー プロパティを設定するかの関数は、Visual Studio を終了するように求めるダイアログ ボックスを表示します。  
  
## 参照  
 [Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)