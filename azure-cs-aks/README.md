[![Deploy](https://get.pulumi.com/new/button.svg)](https://app.pulumi.com/new)

# Azure Kubernetes Service (AKS) Cluster

Stands up an [Azure Kubernetes Service](https://azure.microsoft.com/en-us/services/kubernetes-service/) (AKS) cluster.

## Deploying the App

To deploy your infrastructure, follow the below steps.

### Prerequisites

1. [Install Pulumi](https://www.pulumi.com/docs/get-started/install/)
2. [Install .NET Core 3.0+](https://dotnet.microsoft.com/download)

### Steps

1. Create a new stack:

    ```sh
    $ pulumi stack init
    Enter a stack name: dev
    ```

1. Set the required configuration variable for this program:

    ```bash
    $ pulumi config set azure:location westus
    $ az login
    ```

4. Stand up the AKS cluster:

    ```bash
    $ pulumi up
    ```

5. After 10-15 minutes, your cluster will be ready, and the kubeconfig YAML you'll use to connect to the cluster will be available as an output. You can save this kubeconfig to a file like so:

    ```bash
    $ pulumi stack output kubeconfig > kubeconfig.yaml
    ```

    Once you have this file in hand, you can interact with your new cluster as usual via `kubectl`:

    ```bash
    $ KUBECONFIG=./kubeconfig.yaml kubectl get nodes
    ```
6. From there, feel free to experiment. Simply making edits and running `pulumi up` will incrementally update your stack.

7. Once you've finished experimenting, tear down your stack's resources by destroying and removing it:

    ```bash
    $ pulumi destroy --yes
    $ pulumi stack rm --yes
    ```
