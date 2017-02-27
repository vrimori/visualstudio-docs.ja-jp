---
title: "タスクの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 作成 (タスクを)"
  - "MSBuild, 記述 (タスクを)"
  - "タスク, 作成 (MSBuild 用に)"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# タスクの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

タスクでは、ビルド プロセスの間に実行するコードを指定します。  タスクはターゲット内に含まれます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] には一般的なタスクのライブラリが含まれていますが、独自にタスクを作成することもできます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に付属のタスク ライブラリの詳細については、「[Task Reference](../msbuild/msbuild-task-reference.md)」を参照してください。  
  
## タスク  
 タスクの例として、1 つ以上のファイルをコピーする [Copy](../msbuild/copy-task.md)、ディレクトリを作成する [MakeDir](../msbuild/makedir-task.md)、[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ソース コード ファイルをコンパイルする [Csc](../msbuild/csc-task.md) などがあります。  各タスクは、<xref:Microsoft.Build.Framework.ITask> インターフェイスを実装する .NET クラスとして実装されます。これは、Microsoft.Build.Framework.dll アセンブリで定義されます。  
  
 タスクを実装する際には、次の 2 つの手法があります。  
  
-   <xref:Microsoft.Build.Framework.ITask> インターフェイスを直接実装する。  
  
-   ヘルパー クラス <xref:Microsoft.Build.Utilities.Task> からクラスを派生させる。これは、Microsoft.Build.Utilities.dll アセンブリで定義されます。  タスクは ITask を実装し、一部の ITask メンバーの既定の実装を提供します。  さらに、ログ記録が簡単になります。  
  
 どちらの場合も、`Execute` という名前のメソッドをクラスに追加する必要があります。これはタスクの実行時に呼び出されるメソッドです。  このメソッドはパラメーターを受け取らず、`Boolean` 値を返します。タスクが成功した場合は `true`、失敗した場合は `false` です。  次の例は、アクションを実行せずに `true` を返すタスクを示します。  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 次のプロジェクト ファイルは、このタスクを実行します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 実行されたタスクは、タスク クラスで .NET プロパティを作成した場合は、プロジェクト ファイルから入力を受け取ることができます。  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] は、これらのプロパティを直ちに設定してから、タスクの `Execute` メソッドを呼び出します。  文字列プロパティを作成するには、次のようなタスク コードを使用します。  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 次のプロジェクト ファイルはこのタスクを実行し、`MyProperty` に特定の値を設定します。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## タスクの登録  
 プロジェクトがタスクを実行する場合は、タスク クラスを含むアセンブリの検索方法を [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] が認識している必要があります。  タスクは [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md) を使用して登録されます。  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] の Microsoft.Common.Tasks ファイルは、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に組み込まれたすべてのタスクを登録する `UsingTask` 要素の一覧が収められたプロジェクト ファイルです。  このファイルは、すべてのプロジェクトのビルド時に自動的にインクルードされます。  Microsoft.Common.Tasks に登録されているタスクが現在のプロジェクト ファイルにも登録されている場合は、現在のプロジェクト ファイルが優先されます。つまり、既定のタスクを同じ名前の独自のタスクでオーバーライドできます。  
  
> [!TIP]
>  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に含まれるタスクの一覧を表示するには、Microsoft.Common.Tasks の内容を表示します。  
  
## タスクからのイベントの生成  
 タスクが <xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生する場合は、<xref:Microsoft.Build.Utilities.Task> クラスで次のヘルパー メソッドのいずれかを使用して、任意の登録済みロガーによって取得および表示されるイベントを生成できます。  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 タスクが <xref:Microsoft.Build.Framework.ITask> を直接実装する場合も、そのようなイベントを生成できますが、IBuildEngine インターフェイスを使用する必要があります。  次の例に、ITask を実装し、カスタム イベントを生成するタスクを示します。  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## 設定する必須のタスク パラメーター  
 特定のタスク プロパティを "required" とマークすると、タスクを実行するすべてのプロジェクト ファイルでそのプロパティの値を設定する必要があり、設定しない場合はビルドが失敗します。  次のように `[Required]` 属性をタスクの .NET プロパティに適用します。  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 `[Required]` 属性は、<xref:Microsoft.Build.Framework> 名前空間の <xref:Microsoft.Build.Framework.RequiredAttribute> によって定義されます。  
  
## 例  
  
### Description  
 次の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生したタスクを示します。  このタスクは `true` を返して、成功したことを示します。  
  
### コード  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## 例  
  
### Description  
 次の [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Framework.ITask> インターフェイスを実装するタスクを示します。  このタスクは `true` を返して、成功したことを示します。  
  
### コード  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## 例  
  
### Description  
 この [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] クラスは、<xref:Microsoft.Build.Utilities.Task> ヘルパー クラスから派生したタスクを示します。  必須の文字列プロパティがあり、すべての登録済みロガーによって表示されるイベントを生成します。  
  
### コード  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## 例  
  
### Description  
 次の例は、前に示したタスクの例 SimpleTask3 を呼び出すプロジェクト ファイルを示します。  
  
### コード  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## 参照  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)